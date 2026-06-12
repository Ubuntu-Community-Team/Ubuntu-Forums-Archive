---
title: "asus eeepc x101 owners cat /proc/acpi/battery/BAT0"
date: 2013-01-22
forum: The Cafe
---

### Post by 0800peter on 2013-01-22
Hopefully not at the wrong place I m looking for some informations about laptop battery of an asus x101 model e.g. a31-x101. that is a 3 cell one.

Mine has given up recently just 30 minutes left :-( after 9 months powerusing
The prices for this type of batt ranges from ~40 - 90 Eur. Thats a lot I thougt
so why not hacking the batt. 
I checked   cat /proc/acpi/battery/BAT0/info and saw just some 800 mA last full capacity. 
So I decided to open the plastic and check the malicious cell. It was a hard work to open the case and keep the batt working. Then I connected a cell-logger with some soldering and found the middle cell more than 400mV difference to the right one. Without load!.
The cell-logger told me the laptop-charging algorithm is not balancing the cells. 
So i connected the removed batt to a separate lipo balancer charger.
Still all cells left soldered in the case a retry after balancing told  1670mA last full capacity that was feeled too optimistic due to just some minutes more now without adapter.

Finaly I changed the cells with some i know are good . And  bricked the batt. :((

So far still some information is present but no supply, and no charging.
 The voltage reading is exactly the one the cell-logger reports. 
But the serial number is missing now, and the cycles is set to 0

The net told me lots of stuff about the batt controllers possibilities, but so far i have no idea which one is really inside nor how to make the reset.

May someone post a working batterys info or more if you can generate somehow. 

My goal would be to bring the "repaired" batt back to life and then donate half the price of a new batt bucks to a human organization. 

here what is left 

>cat /proc/acpi/battery/BAT0/info 
present:                 yes
design capacity:         2600 mAh
last full capacity:      1670 mAh
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 10 mAh
design capacity low:     5 mAh
cycle count:          0
capacity granularity 1:  26 mAh
capacity granularity 2:  26 mAh
model number:            X101
serial number:            
battery type:            LION
OEM info:                ASUS

>cat /proc/acpi/battery/BAT0/state 
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            0 mA
remaining capacity:      1571 mAh
present voltage:         12192 mV

>acpi -b   
Battery 0: Charging, 94%, charging at zero rate - will never fully charge.

tools used and opened cellpack
[IMG]http://666kb.com/i/cay0v0kz8d59rs685.jpg[/IMG]

 Cell-logger attached shows number 2 has a low voltage 
[IMG]http://666kb.com/i/cay1526ekp72xrlad.jpg[/IMG]

Here the batt is discharging with the logger attached
[IMG]http://666kb.com/i/cay1lzs8lv65uo491.jpg[/IMG]

Finally this is what is left by now, nice view no charging no discharging in the netbook
[img]http://666kb.com/i/cay1u7uvgws0h43ut.jpg[/img]


peter

---

