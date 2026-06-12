---
title: "See yahoo weather in your terminal"
date: 2007-02-10
forum: The Cafe
---

### Post by Flatline-kun on 2007-02-10
I wrote a little program to view the weather feed from Yahoo in a terminal window. It will also work as a plug-in to Conky. It uses Curl and XSLT, so you have to have them installed.

Flatline

---

### Post by Zeronline on 2009-05-24
Nice little doodad here. Installed and works perfectly! Saves me from having to bring up the web every time.

Thanks!

---

### Post by pwnst*r on 2009-05-24
screenshot?

---

### Post by sisco311 on 2009-05-24
i'm using weather-util:
```
weather -i LRSM
Current conditions at Romania (LRSM) 47-48N 022-53E 124M (LRSM)
Last updated May 24, 2009 - 11:00 AM EDT / 2009.05.24 1500 UTC
   Temperature: 66 F (19 C)
   Relative Humidity: 42%
   Wind: from the W (260 degrees) at 7 MPH (6 KT) (direction variable)
   Sky conditions: mostly cloudy

```

and weatherget in arch:
```
weatherget -s ROXX0038 --metric
Satu Mare, Romania  (22.89, 47.79)
Satu Mare, ROMANIA  5/24/09 6:00 PM Local Time
  Temperature    : 19 C
  Feels Like     : 19 C
  Conditions     : Mostly Cloudy
  Wind           : 11 km/h, 0 km/h gusts, W
  Visibility     : 10.0 km
  Humidity       : 43 %
  Barometer      : 1019.0 mb, falling
  Dewpoint       : 6 C
  UV             : Low, 1
  Sunrise        : 5:41 AM
  Sunset         : 9:11 PM
  Moon           : New
  Time Zone      : 3 GMT

```

notify-osd + weatherget:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=114945&stc=1&d=1243179358[/IMG]

---

### Post by sisco311 on 2009-05-24
i've tried the script and it works very well.


```
./weather 
Satu Mare, * (6:30 pm EEST):
  Partly Cloudy, 20°C (Feels Like: 18°C)
  Wind - W 14kph
  Barometer - 1016mb and steady
  Sunset: 9:10 pm
Forecast:
    Today - Partly Cloudy
            High of 21°C, low of 10°C
 Tomorrow - Mostly Sunny
            High of 25°C, low of 11°C

```

---

