## The purpose of this task is to filter down the data for California from a list of all the states. Specifically I want to filter the data for all the counties in CA only
Reference:
https://stackoverflow.com/questions/17071871/select-rows-from-a-dataframe-based-on-values-in-a-column-in-pandas
----
#### I'm using python2 locally


```python
import pandas as pd

# Open the desired file to filter from. File is provided in the repo
iris=pd.read_csv("geography.csv")

# Create a list to match from. In this case I only have 1 item.
tomatch=["CALIFORNIA"]

# Filter IF the Column 'State' = CALIFORNIA
new= iris.loc[iris['State'].isin(tomatch)]

# print results
new

```
This will reduce the list from 5000 something items ----> 50 something items

```
           State   CountyTownName  
406   CALIFORNIA           ALPINE  
407   CALIFORNIA           AMADOR  
408   CALIFORNIA        CALAVERAS  
409   CALIFORNIA           COLUSA  
410   CALIFORNIA        DEL NORTE  
411   CALIFORNIA            GLENN  
412   CALIFORNIA         HUMBOLDT  
413   CALIFORNIA             INYO  
414   CALIFORNIA             LAKE  
415   CALIFORNIA           LASSEN  
416   CALIFORNIA         MARIPOSA  
417   CALIFORNIA        MENDOCINO  
418   CALIFORNIA            MODOC  
419   CALIFORNIA             MONO  
420   CALIFORNIA           NEVADA  
421   CALIFORNIA           PLUMAS  
422   CALIFORNIA           SIERRA  
423   CALIFORNIA         SISKIYOU  
424   CALIFORNIA           TEHAMA  
425   CALIFORNIA          TRINITY  
426   CALIFORNIA         TUOLUMNE  
1422  CALIFORNIA          ALAMEDA  
1423  CALIFORNIA     CONTRA COSTA  
1424  CALIFORNIA      LOS ANGELES  
1425  CALIFORNIA            MARIN  
1426  CALIFORNIA           ORANGE  
1427  CALIFORNIA    SAN FRANCISCO  
1428  CALIFORNIA        SAN MATEO  
3295  CALIFORNIA            BUTTE  
3296  CALIFORNIA        EL DORADO  
3297  CALIFORNIA           FRESNO  
3298  CALIFORNIA         IMPERIAL  
3299  CALIFORNIA             KERN  
3300  CALIFORNIA            KINGS  
3301  CALIFORNIA           MADERA  
3302  CALIFORNIA           MERCED  
3303  CALIFORNIA         MONTEREY  
3304  CALIFORNIA             NAPA  
3305  CALIFORNIA           PLACER  
3306  CALIFORNIA        RIVERSIDE  
3307  CALIFORNIA       SACRAMENTO  
3308  CALIFORNIA       SAN BENITO  
3309  CALIFORNIA   SAN BERNARDINO  
3310  CALIFORNIA        SAN DIEGO  
3311  CALIFORNIA      SAN JOAQUIN  
3312  CALIFORNIA  SAN LUIS OBISPO  
3313  CALIFORNIA    SANTA BARBARA  
3314  CALIFORNIA      SANTA CLARA  
3315  CALIFORNIA       SANTA CRUZ  
3316  CALIFORNIA           SHASTA  
3317  CALIFORNIA           SOLANO  
3318  CALIFORNIA           SONOMA  
3319  CALIFORNIA       STANISLAUS  
3320  CALIFORNIA           SUTTER  
3321  CALIFORNIA           TULARE  
3322  CALIFORNIA          VENTURA  
3323  CALIFORNIA             YOLO  
3324  CALIFORNIA             YUBA 
```

Now let's output the results to a csv file

```python
new.to_csv(path_or_buf="Cali-counties.csv")
```

The resulting file is  uploaded in this repo named "Cali-counties.csv"


Now, let's create a list out of all the area code in the new dataframe

```python
#declare an empty array 
area_list=[]

#append the list of the AreaCodes to the list
areaList = new['Area'].tolist()
```


This time , I have a larger file with about 500,000 items. I'm filtering items that match the Area code in the areaList array.\

So let's load that file first:

```python

new_bigList=pd.read_csv("ALC_Export.csv")

```

Now let's filter out the desired items just like we did earlier
```python
# Filter IF the area is in the areaList
filtered_bigList= new_bigList.loc[new_bigList['Area'].isin(areaList)]
           
 ```
 
 The length of items went from 484,390 ---->27,914
 
 
 
           

