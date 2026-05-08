# ETL Pipeline for Snowflake Data Integration
#### Project Overview
This project implements an end-to-end ETL pipeline for extracting, transforming, and loading (ETL) sales data from a CSV file into a Snowflake database. The pipeline is built using Python and pandas for data manipulation and includes comprehensive data cleaning, transformation, and post-load validation steps to ensure consistency and data integrity.
#### Key Features:
-  Data Extraction: Pulls sales data from a CSV file.

-  Data Transformation: Cleans and prepares the data by handling missing values, converting date formats, and adding calculated columns (e.g., Delivery Time in Days).

-  Data Loading: Efficiently loads transformed data into a Snowflake database, avoiding duplicates and ensuring data consistency.

-  Post-Load Validation: Verifies data integrity by checking for NULL values and duplicate rows after loading into Snowflake.

#### Credentials & Security:

-  .env File: Sensitive credentials and configurations (e.g., Snowflake login details) are securely managed using the .env file.

-   The .env.example.txt file is provided as a template for setting up environment variables without exposing sensitive information.

#### Project Structure
###### The repository contains the following key files:

 - **ETL_Pipeline.ipynb:** The main Jupyter notebook containing the complete ETL pipeline code.

 - **Data/**: Folder containing the source sales CSV file used for the ETL process.

 - **README.md:** This file, providing an overview of the project.

 - **requirements.txt:** A list of Python dependencies required to run the project.

 - **.gitignore:** Ensures sensitive files like .env are not uploaded to GitHub.

 - **.env.example.txt:** A template for the .env file, ensuring secure handling of configuration details.

 - **.gitattributes:** Optional configuration for Git handling.

#### Installation
1. Clone the repository:
git clone https://github.com/kowshiksam7/ETL_Snowflake_Project_CSV.git
2. Install the required dependencies:
Ensure you have Python 3.x installed, then create a virtual environment and install dependencies:

##### Create a Virtual Environment:

- python -m venv venv

##### Activate the virtual environment

     - On Windows:
       venv\Scripts\activate

     - On macOS/Linux:
       source venv/bin/activate

 ###### Install the required packages:
 
     - pip install -r requirements.txt

3. Set up the environment variables:
   
   - Copy .env.example.txt to .env and update the file with your Snowflake credentials.
   - cp .env.example.txt .env

##### Ensure that the following environment variables are correctly set in your .env file:

   - SNOWFLAKE_ACCOUNT: Your Snowflake account URL.

   - SNOWFLAKE_USER: Your Snowflake username.

   - SNOWFLAKE_PASSWORD: Your Snowflake password.

   - SNOWFLAKE_WAREHOUSE: Snowflake warehouse to be used.

   - SNOWFLAKE_DATABASE: Your Snowflake database.

   - SNOWFLAKE_SCHEMA: The schema for loading data.

4. Run the ETL pipeline:
   - Once your environment is set up and the credentials are in place, run the ETL_Pipeline.ipynb Jupyter notebook to execute the entire ETL process.

#### Project Workflow
1. Data Extraction:
   - The pipeline begins by loading sales data from a CSV file located at the path specified in the .env file.

2. Data Transformation:
   - Missing values in the Postal Code column are filled with 0.

   - The Order Date and Ship Date columns are converted to datetime format.

   - New columns are added:

      - Order_Month: Extracted from the Order Date.

      - Delivery Time (Days): Calculated as the difference between the Ship Date and Order Date.

3. Data Loading:
   - The transformed data is then loaded into a Snowflake database. The pipeline checks for existing ROW_ID values to avoid duplicate entries.

4. Post-Load Validation:
   - After loading the data, the pipeline performs integrity checks:

       - Verifies that no NULL values exist in critical fields.

       - Compares the SALES sum between the source CSV file and the Snowflake table.

       - Checks for duplicate ROW_ID values in the Snowflake database.

#### Notes:

-  Data Integrity: The pipeline ensures that data is consistently transformed, loaded, and validated to maintain high data quality.

-  Scalability: This pipeline can be easily extended or adapted for use with different datasets or databases.

### Author

- This project was developed by **Kowshik Samudrala**.  
- You can reach me via email at kowshikteja7@gmail.com or connect with me on LinkedIn(www.linkedin.com/in/kowshik-s-a539b21aa)


