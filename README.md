# Movie Review Analysis with NYT & TMDB APIs

**1. Overview**

- This Python project fetches movie reviews from The New York Times (NYT) API and enriches them with data from The Movie Database (TMDB) API. 
- The goal is to combine information from both sources to create a dataset for analysis of movie reviews and their corresponding metadata.

**2. Project Structure

`your_script.ipynb:` Main notebook containing the code.

`.env:` File to store your API keys (optional, see below). --- please, create your own separately.

`nyt_movie_reviews_tmdb.csv:` Output CSV file with the merged and cleaned data.

3. Dependencies

`requests`\
`time`\
`pandas`\
`json`\
`urllib.parse (for URL encoding)`\
`pandas.json_normalize`\
`dotenv (optional, to load API keys from .env file)`\

4. How to Use

### Obtain API Keys:

Get an API key from The New York Times Developer Network: https://developer.nytimes.com/ \
Get an API key from The Movie Database: https://www.themoviedb.org/documentation/api \
Set Up Environment Variables (Optional): \

- Create a .env file in the project directory.

- Add the following lines, replacing YOUR_NYT_API_KEY and YOUR_TMDB_API_KEY with your actual keys:

**NYT_API_KEY=YOUR_NYT_API_KEY**

**TMDB_API_KEY=YOUR_TMDB_API_KEY**

If you don't want to use a .env file, you can directly assign the values to the nyt_api_key and tmdb_api_key variables in the script.

----
### Run the notebook:

Execute `retrieve_movie_data.ipynb` to fetch movie reviews from the NYT API and enrich them with data from the TMDB API.

The script will:
a. Fetch movie reviews from the NYT API, filtering for reviews mentioning "love" and published within a specified date range.

b. Extract movie titles from the reviews.

c.Use the TMDB API to fetch additional data for each movie (budget, genres, etc.).

d.Merge the NYT and TMDB data into a single DataFrame.

e.Clean the data (remove list formatting, drop duplicates).

f. Save the merged and cleaned data to nyt_movie_reviews_tmdb.csv.

----
**Code Structure**
Imports:

Necessary libraries are imported.

API Key Configuration:

API keys are loaded from the .env file (if used) or assigned directly.

**NYT API Request:** Parameters for the NYT API request are defined.

- A loop iterates through pages of results, making requests with rate limiting.

- Movie reviews are extracted and processed.

**TMDB API Request:** For each movie title, a search is performed on the TMDB API to find its ID.

- Using the movie ID, detailed information is retrieved.

- The data is organized into a list of dictionaries.

- Data Cleaning and Export:

- The list of movie data is converted into a Pandas DataFrame.

- The NYT and TMDB DataFrames are merged on the title column.

- List-like formatting is removed from specific columns.

- Duplicate rows are dropped.

- The final DataFrame is exported to a CSV file.

------
**Important Notes**

Rate Limits: Respect the rate limits of both the NYT and TMDB APIs. The script includes mechanisms to pause execution and avoid exceeding these limits.

Error Handling: The script has error handling to deal with cases where movies are not found or data is missing/incomplete.

Customization: You can modify the filters for the NYT API query (e.g., change the keyword, date range) to suit your specific interests.

----
developed by Roberto dos Reis @rmsreis