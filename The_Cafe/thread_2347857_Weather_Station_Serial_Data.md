---
title: "Weather Station Serial Data"
date: 2016-12-29
forum: The Cafe
---

### Post by Axi&#8594; on 2016-12-29
I've bought an Argent Data Weather Station that has wind speed/wind direction/ Rain/Temp sensors
I am having an issue with the wind speed sensor. I currently have a USB to serial db9 cable plugged into the ADS-WS1 weather station and using puttytel I can read the wind direction, rainfall, temperature and humidity data. But as soon as the wind speed sensor begins to move it seems to generate "interference" I get a strange character appearing in the terminal, and it seems to pause/crash the unit. Any ideas?


[https://www.argentdata.com/catalog/product_info.php?products_id=135](https://www.argentdata.com/catalog/product_info.php?products_id=135)

[ATTACH=CONFIG]272894[/ATTACH]

---

### Post by Axi&#8594; on 2016-12-31
[COLOR=#000000][FONT=&quot]Hi Guys,[/FONT][/COLOR][COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Just wanted to let you know I found the issue.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]I found a couple of solder bridges one was spanning pin 2 and 3 which is the wind speed and reset pins. [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]I've cleared the bridge and the strange character has gone. I'll run it for a while before I confirm that it's fixed :) [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Thanks[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Sean

[IMG]https://postimg.org/image/c5f1h5h8v/[/IMG][/FONT][/COLOR]

---

