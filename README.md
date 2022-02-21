# ETL (Extract, Transform, Load) data pipeline process 
## Purpose of the analysis:
ETL involved transformation of raw data that exists in multiple places in to a more clean, structured format before it can be analyzed. There  are three steps in this process: Extract, Transform, and Load. 

In this analysis, large data from Wikipedia and Kaggle was gathered, cleaned, transformed, combined and saved into a SQL database. This helps in preparing the large set of data for further analysis such as finding low budget movies with high rating. This will help the organization involved in making right decision on buying movies. 

A separate file with Various functions has also been performed to automate this process in the future if needed.

## Resources:
wikipedia_movies.json

movies_metadata.csv from Kaggle

ratings.csv from Kaggle

amazing prime movies.ipynb - File for ETL process
ETL_clean_kaggle_data.ipynb - File for functions to facilitate the ETL process
ETL_create_database.ipynb - function to create database of the data

## Methods and Results:
PROCESS 1: EXTRACT
- data 1: Wikipedia_movies.json
- As this is a webscraped data lot of work was needed to clean up the data and make it usable.
- There are 193 columns in the raw data set
- As  imdb_link and director columns are very essential for  the data, columns that do not have both these values were removed.

- ![image](https://user-images.githubusercontent.com/94877067/154876910-a3282d13-0208-4e7d-9c0b-ab1fbe9a931d.png)

 -This step reduced the number of columns to 78
 - The data set was then cleaned to remove columns that has alternative titles of the movie (repeteitve data).
 - A function was defined to iterate through the json data and remove columns with alternative titles
 

![image](https://user-images.githubusercontent.com/94877067/154877110-878272f5-f8b2-4a27-99f5-0f44d748dd6a.png)


-Repetetive columns were also merged by defining function within a function


![image](https://user-images.githubusercontent.com/94877067/154877294-e95c0792-90f2-42a3-af35-847943e0f4d9.png)


-Json data was converted to dataframe and further cleaning was done
- datatype errors were then cleaned and formatted  using Regex expressions. 
- data 2 & 3: Kaggle metadata  and ratings - csv file
- df.dtypes helped us determine the datatypes of the columns
- Columns with bad data was removed and datatype errors were alos fixed.
- the datatype error of the timestamp column with dates was fixed using the to_datetime()

Merging of data:
The cleaned wikipedia data and kaggle meta data was merged using pd.merge on "imdb_id)
The redundant columns in the merged dataframe were then cleaned. The columns from wikipedia and kaggle metadata were carefully compared and appropriate actions were taken.

![image](https://user-images.githubusercontent.com/94877067/154879084-1845c33e-5d18-4097-9b93-9d4936e02172.png)


Ratings data was also then merged with movie_df
**Connect Pandas and SQL**

Easiest way of having the cleaned, transformed, merged data available for further analysis is to have it in a SQL database.
The  data  is then mpved from the Pandas into a PostgresSQL database


![image](https://user-images.githubusercontent.com/94877067/154879464-942fceef-92ae-416f-8b0d-52d1e2bac34d.png)




