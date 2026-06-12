---
title: "Hobbit Graph"
date: 2008-10-20
forum: Server Platforms
---

### Post by luccom on 2008-10-20
I am trying to display graph for the temperature read by sensors but it is not showing up. 
This is the data on the Web page (Sonde_Admin.temp)
```
Mon Oct 20 11:43:38 2008
Sonde_Admin

Fumee:OK
Temp_Externe:21.1
Eau:0.1
Temp_Local:19.1
Humidity:44.5
```

this is my bb-hosts
```
10.30.43.102 Sonde_Admin        # temp TRENDS:*,temp

my hobbitserver.cfg
TEST2RRD="cpu=la,... ,temp=ncv"
NCV_temp="TempExterne:GAUGE,Eau:GAUGE,TempLocal:GAUGE,Humidity:GAUGE"
GRAPHS="la,... temp"
```

my hobbitgraph.cfg
```
[temp]
       TITLE Temperature
       YAXIS Deg Celsius
       DEF:TempLocal=sensors.rrd:TempLocal:AVERAGE
       LINE2:TempLocal#FF0000:Temp Local
       GPRINT:TempLocal:LAST: \: %5.1lf (cur)
       GPRINT:TempLocal:MAX: \: %5.1lf (max)
       GPRINT:TempLocal:MIN: \: %5.1lf (min)
       GPRINT:TempLocal:AVERAGE: \: %5.1lf (avg)\n
```

The data is collecte in the rrd file /var/lib/hobbit/rrd/Sonde_Admin/temp.rrd

 ```
               <name> TempLocal </name>
                <type> GAUGE </type>
                <minimal_heartbeat> 600 </minimal_heartbeat>
                <min> 0.0000000000e+00 </min>
                <max> NaN </max>

                <!-- PDP Status -->
                <last_ds> 19.2 </last_ds>
                <value> 3.1235000000e+03 </value>
                <unknown_sec> 0 </unknown_sec>

```
The only thing I am getting it the line (hobbit graph ncv:temp) at the bottom of the page but no graph. What am I missing ?

---

### Post by skliarie on 2009-07-13
Have you found solution to the problem? I have exactly the same output as you...

---

