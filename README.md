# ETL Weather Data Pipeline using Apache Airflow


## Overview
This project demonstrates an ETL (Extract, Transform, Load) pipeline to fetch weather data from the Open-Meteo API, transform it, and load it into a PostgreSQL database using Apache Airflow. The goal is to showcase automated data workflows and gain hands-on experience with real-time data pipelines.

## Key Features
**Extract**: Fetch weather data (temperature, wind speed, etc.) from Open-Meteo's API for a specific location.

**Transform**: Structure the raw JSON response into meaningful fields for analysis.

**Load**: Store the transformed data in a PostgreSQL database for further use.

**Automation**: The entire ETL process is orchestrated and automated using Airflow.

## Project Architecture
1. Airflow DAG: The pipeline consists of three tasks:

      * extract_weather_data: Calls the Open-Meteo API to fetch weather data.
      * transform_weather_data: Extracts relevant data points and prepares them for storage.
      * load_weather_data: Loads the transformed data into a PostgreSQL database.

2. Database:
PostgreSQL database stores the weather data with the following fields:

      * latitude (FLOAT)
      * longitude (FLOAT)
      * temperature (FLOAT)
      * windspeed (FLOAT)
      * winddirection (FLOAT)
      * weathercode (INT)
      * timestamp (TIMESTAMP)

## Technologies Used

    * Apache Airflow: Orchestrates the ETL workflow.
    * PostgreSQL: Stores the transformed weather data.
    * Open-Meteo API: Provides real-time weather data.
    * Python: Handles data extraction, transformation, and loading.

## Setup and Installation

### Prerequisites:
  * Python 3.x
  * Apache Airflow installed and configured
  * PostgreSQL database (running and accessible)
  * Airflow connections configured:
  * PostgreSQL: postgres_default
  * HTTP API: open_meteo_api

### Installation Steps:
  
1. Clone the Repository:
  
        gh repo clone raghava000/raghava.github.io

2. Set up Airflow and PostgreSQL:

  * Ensure Airflow is installed and running.
  * Create a PostgreSQL connection in Airflow with the ID postgres_default.
  * Add an HTTP connection in Airflow for the Open-Meteo API with ID open_meteo_api.

3. Trigger the DAG:

  * Access the Airflow UI at http://localhost:8080.
  * Enable and manually trigger the weather_etl_pipeline DAG.


### Usage and Execution Flow
  1. The DAG fetches weather data from the API.
  2. Transforms the JSON data to extract key weather metrics.
  3. Loads the cleaned data into the PostgreSQL table weather_data.

### Troubleshooting
  * Connection Refused Error: Ensure PostgreSQL is running and accepting connections on the correct port.
  * Airflow Webserver Issues: If Airflow is already running on a different port, use:

          sudo lsof -i :8080  # Find the process ID (PID)
          sudo kill -15 <PID>  # Stop the process running on that port


### Project Output

Sample data entry in the PostgreSQL table:

Latitude	Longitude	Temperature	Windspeed	 Wind Direction	 Weather Code	     Timestamp

51.5074	  -0.1278	   15.2°C	    10.5 km/h	     230°	            2	       2024-10-23 04:56:42

### Future Improvements
  * Add visualization dashboards with tools like Power BI or Tableau.
  * Extend the ETL to process historical weather data.
  * Automate alerts for extreme weather events.
