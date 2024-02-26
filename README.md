This project is an attempt to predict the rate of foreclosures per 1,000 residents at the census tract level based on demographic, income and housing characteristics derived from American Community Survey data.

Given the post-pandemic surge in foreclosures in the eastern suburbs of Washington, DC, a predictive model capable of forecasting where to direct pre-foreclosure mitigation efforts could prevent the externalities associated with foreclosure for hundreds of households.

Similar models have existed for decades, but these models are often location-specific and focus on demographic and income variables rather than housing characteristics. Given the possibility of a link between suburban development patterns and foreclosures, this project explores the role of housing size and census tract-level growth in housing units as possible proxies for forces that drive foreclosures.

# What does this code do? 

At present, it performs six basic tasks:

1. Reading in a dataset of foreclosures provided by the Prince George's County planning department, a dataset of geolocated addresses corresponding to the addresses in the Prince George's County foreclosures dataset, and a pre-engineered .csv file containing selected housing characteristics from the 2022 American Community Survey.

2. Joining the foreclosure dataset with the geolocation information, including tract code, with 23 individual variables pulled from previous American Community Surveys using a Census API key, and with the separate dataset of housing characteristics.

3. De-duplicating records present in the original dataset or created in the joining process.

4. Filtering rows with missing values necessary to calculate the dependent variable, including census tract identification numbers and population estimates.

5. Filtering rows with census tract identification numbers that do not match the Census' 2020 list of Prince George's County tracts.

6. Plotting the distribution and quintiles of the dependent variable (foreclosures per 1,000 residents at the census tract level). 


# In order to run the code, you will need a Census API key. 

In this code, the API key is stored locally for security. If you do not have a Census API key, you can obtain one here: https://api.census.gov/data/key_signup.html

To securely store your Census API key rather than calling it every time you fetch Census data, you can: 

# Use the tidycensus package:

# Install your API key (replace "111111abc" with your actual key)
census_api_key("111111abc", install = TRUE)

# Reload your environment to use the key without restarting R
readRenviron("~/.Renviron")

# Check if the key is set
Sys.getenv("CENSUS_API_KEY")


# Mannually set the key in your .renviron file:

# Open your .Renviron file (create one if it doesn’t exist).
Add the following line (replace PASTEYOURKEYHERE with your actual key): CENSUS_KEY=PASTEYOURKEYHERE

Save the file.

Reload your .Renviron by running: readRenviron("~/.Renviron")

Verify that the key is correctly set: Sys.getenv("CENSUS_KEY")
