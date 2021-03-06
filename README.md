# route-optimization

This repo solves the vehicle routing problem and was implemented for a large Canadian freight company. We take a manifest of deliveries to be made in a day and produce an set of individual manifests and routes for a fleet of trucks. The algorithms can account for vehicle capacities, and having multiple truck depots to dispatch from. Our optimized solution represented a 5% decrease of travel distance on average compared to previous practice at the company, amounting to significant fuel savings.

First we clean the manifest data, a list of deliveries to be made, in the geocodepandas.py file. This fills in missing latitude/longitude data for the delivery locations by geocoding addresses. Then we use GraphHopper to create a distance matrix, an array of distances between each pair of locations in the manifest. Finally, we use the distance matrix to solve the route optimization problem in tsp.py.

Conventions - Address file should start with depot first (starting/ending point for travelling salesman problem (TSP)).

Geocoded file should be in CSV format with (lat/long/address) with the first row being the header "Latitude,Longitude,Address".

Distance matrix file is in CSV format with row/column indices matching that of geocoded file (row=origin, column=destination).

Dependencies: GraphHopper folder assumed to be in same location as dmatrix.jar, with subfolder north-america_canada_ontario-gh containing open source map data from Open Street Maps.

Usage: java -jar dmatrix.jar manifest.csv

produces dmatrix.csv
