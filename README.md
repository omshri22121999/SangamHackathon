# SangamHack

Data could not be uploaded since it was proprietary.

## Team : Alpha AI

### Data pre-processing:

As all the devices work independently, we can assume that types of errors can almost be same for each device.
So, we clean the data seperately for each device.

#### i) Timestamp Correction:

For readings which we have a wrong timestamp can be noticed by difference between the tmstamp and svr_time. We can put a threshold of 2 days (i.e, if difference is more than 2 days) we can change the timestamp to svr_time, as generally it takes at most 20 seconds for uploading.

#### ii) GPS correction:

As we grouped the data by devices, for each reading if we get a wrong co-ordinate (we can check by integral part of co-ordinate) we update it as the previous location itself unless there is a long streak of bad data. It is not bad as device pings every 20 seconds approximately and there will be no big change upto 4th decimal of latitute or longitude.

#### iii) Outlier identification and removal:

For each device, we plotted the scatterplot of all the features. We came to a conclusion that the best way to remove outlier was to __IQR score__.
Thus we varied the lower and upper bound according to the data we saw. If there was no underlier in the data, we can directly push the data as final feature without applying IQR removal. 
