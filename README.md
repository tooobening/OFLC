# Interactive Map Web Application for GIS Specialist Wage Levels

## Overview
This project aims to create an interactive web application that displays the prevailing wage levels for the job title "Geographic Information Systems (GIS) Specialist (SOC Code: 15-1299)" provided by the Department of Labor (DOL) for each county in the United States. The application will feature an interactive map of the US, allowing users to click on a county to view a bar chart showing four different wage levels.

## Purpose
The primary goal of this application is to assist international GIS professionals interested in employer-based sponsorship in the USA. By providing detailed wage information regulated by the Department of Labor, users can better understand the minimum wage levels in their respective areas.

## Features
- Interactive US map with county boundaries
- Clickable counties that display a pop-up with wage levels
- Bar chart representation of the wage levels
- Data sourced from the Department of Labor

## Target Audience
This application is designed for international GIS workers seeking information on employer-sponsored positions and wage levels within specific counties in the United States.

## Technologies Used
- **Python**: For data manipulation and processing
- **GeoPandas**: For handling geographical data
- **Pandas**: For data analysis and manipulation
- **NumPy**: For numerical operations
- **Matplotlib/Plotly**: For visualizing wage data in charts

## Installation
To run this project, you need to have the following Python packages installed. You can install them using pip:

```bash
pip install geopandas pandas numpy matplotlib plotly
Code Overview
1. Saving a GeoDataFrame as a Shapefile
The following function saves a GeoDataFrame as a shapefile in a specified directory:

python
Copy code
def save_shapefile_within_dir(gdf, shapefile_name):
    """
    Saves a GeoDataFrame as a shapefile in a directory named after the shapefile.
    
    Parameters:
    gdf (GeoDataFrame): The GeoDataFrame to be saved.
    shapefile_name (str): The name of the shapefile without extension.
    """
    # Specify the output directory based on the shapefile name
    output_directory = f"C://Projects//OFLC//Data//{shapefile_name}/"
    os.makedirs(output_directory, exist_ok=True)
    output_shapefile = os.path.join(output_directory, shapefile_name + '.shp')
    gdf.to_file(output_shapefile, driver='ESRI Shapefile')
    print(f'Shapefile saved at: {output_shapefile}')
2. Loading Data
Load a shapefile and a CSV file to create a GeoDataFrame:

python
Copy code
# Load shapefile
zip_file_path = "C://Projects//OFLC//Data//us-county-boundaries.zip"
gdf = gpd.read_file(f"zip://{zip_file_path}")

# Load CSV data
df = pd.read_csv('C://Projects//OFLC//Data//CSV//Geography.csv')
3. Data Merging
Combine data from the shapefile and CSV using a left join:

python
Copy code
merged_gdf = gdf.merge(df, left_on=['namelsad', 'stusab'], right_on=['CountyTownName', 'StateAb'], how='left')
4. Data Cleaning and Conversion
Modify the columns to keep relevant information and convert data types as necessary:

python
Copy code
# Convert 'Area' to integer
merged_gdf['Area'] = merged_gdf['Area'].apply(safe_int_convert)
Usage
Clone this repository to your local machine.
Navigate to the project directory.
Run the main script to launch the application and view the interactive map.
Contributing
Contributions are welcome! If you have suggestions for improvements or new features, feel free to open an issue or submit a pull request.

License
This project is licensed under the MIT License. See the LICENSE file for details.

Acknowledgments
Department of Labor (DOL) for providing wage data.
GeoPandas Documentation for geographic data handling.
csharp
Copy code

### Notes:
- Make sure to adjust the paths and other project-specific details as needed.
- You can add any additional sections that might be relevant, such as FAQ, Contact Information, etc.
- Remember to save this content as `README.md` in your repository.
