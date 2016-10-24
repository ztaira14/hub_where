# hub\_where
Hack-A-Week 11: Python script to gather data on Hubway's bike-sharing stations. 

Hack-A-Week 12: Python scripts to plot data gathered in Hack-A-Week 11. 

Reason: I am a Hubway customer, and would like to know when the stations I
frequent are usually low on bikes. It'd also be interesting to plot overall
trends.

Method: I left the script created in Hack-A-Week 11 running on my laptop
for approximately 1 week, from 10/3/2016 to 10/10/2016. For exact dates and
times, the timestamps can be parsed from the log files in the data directory.
I then used Python to parse through the data gathered in order to find
which Hubway stations see the most activity and which Hubway stations are
more full on average.

### Usage:
- (11) Use `python hub_where.py` to run the hub\_where.py file
- (12) Use `python plots/filename.py` to generate the plots in the diagrams
directory

### Features:
- (11) Uses python to gather and save data via Hubway's station\_status URL
- (11) Only saves data when `last_reported` field has changed
- (11) Shortens dict keys in order to save space
- (12) Numerous graph options: size, color, and both

### What it does:
- (11) If `last_updated.txt` file does not exist, creates `last_updated.txt` as well
    as log files for each station
- (11) Checks every 60 seconds if the data has been updated
- (11) If the data has been updated, log any new data in the station log files
- (11) Only add to the station log files if necessary in order to save space
- (12) `1activity_plots.py` calculates station activity based on log file size
and plots it by size, color, and both
- (12) `2occupancy_plots.py` calculates a weighted average of station occupancy
and plots it by size, color, and both

### What it doesn't do:
- N/A

### Included Files:
```
- README.md..................This readme file
- hub_where.py...............Python script to gather data from Hubway
- last_updated.txt...........Text file to hold epoch time stamps
- plots/.....................Python scripts to parse data and generate graphs
- data/......................Data gathered from Hubway
- diagrams/..................Images generated by the scripts in the plots directory
```
### Output:

### Hubway Stations plotted by GPS Coordinates and Activity

According to log size, station 65 was by far the most active. It had 2380
lines of log data. The second most active was station 134, with 1600 lines of
text, and the third most active was station 67 with 1588 lines of text.

Station 65 is right next to the Lawn on the D and the Boston Convention Center.
Station 134 is right next to Copley in the heart of Boston, and station 67 is
the station by MIT's famous Alchemist statue at the end of the Smoot Bridge.

If you look carefully, you can see the Charles River's outline wandering
through the center of all the Hubway stations.  

![alt text][outputimage]
[outputimage]: https://github.com/ztaira14/hub_where/blob/master/diagrams/1activity_by_color_and_size.png "Activity by color and size"

### Hubway Stations Plotted by Average Occupancy from 10/3/16 to 10/10/16

Despite having vastly different amounts of activity, there were no stations
that remained empty or full throughout the entire week. Most of them were
about 20% to 70% full at any given time. If you look at the plot, though,
the stations in terms of average occupancy are extremely close together
relative to the amount of activity each one gets.

On average, the least occupied Hubway areas are on the MIT side of the Charles,
by the Boston's Children's Museum, and by the Boston's Children's Hospital/Harvard
Medical School/Massachusetts College of Art and Design. 

In the diagrams directory, there are also additional plots that show an
hour-by-hour graph of how occupied each Hubway station is. Based on trends
shown in these graphs, the low-occupancy areas listed above seem to be the most
occupied at night. 

![alt text][outputimage2]
[outputimage2]: https://github.com/ztaira14/hub_where/blob/master/diagrams/2occupancy_by_color_and_size.png "Occupancy by color and size"

![alt text][outputimage3]
[outputimage3]: https://github.com/ztaira14/hub_where/blob/master/diagrams/3occupancy_graph.png "Occupancy bar graph"
