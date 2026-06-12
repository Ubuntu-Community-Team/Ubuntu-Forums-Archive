---
title: "gazp8 battery issues"
date: 2014-07-17
forum: System76 Support
---

### Post by insanengineer on 2014-07-17
Has anyone had any issues with their Gazelle Pro battery (GAZP8)? My laptop is a little over a year old and the battery is already at 37% charge capacity. Did I get a bad battery or are the stock batteries prone to a high amount degregation in a short amount of time? 

[IMG]http://i58.tinypic.com/2rhpr0h.png[/IMG]

---

### Post by isantop on 2014-07-21
Battery life and longevity will vary greatly between different computers (even of the same model). What sort of battery life are you seeing from the system?

---

### Post by cocoder2 on 2014-07-22
I'm also seeing poor battery life on my gazp8.  I'm getting a little over an hour with "normal" use, and less than an hour if watching video or doing a lot of code compiling.  See upower output below...


[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]$ upower -i /org/freedesktop/UPower/devices/battery_BAT0[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]  native-path:          BAT0[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]  vendor:               NOTEBOOK[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]  model:                BAT[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]  serial:               0001[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]  power supply:         yes[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]  updated:              Tue 22 Jul 2014 09:38:50 AM MDT (6 seconds ago)[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]  has history:          yes[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]  has statistics:       yes[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]  battery[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]    present:             yes[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]    rechargeable:        yes[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]    state:               discharging[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]    energy:              22.4997 Wh[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]    energy-empty:        0 Wh[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]    energy-full:         24.8085 Wh[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]    energy-full-design:  48.84 Wh[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]    energy-rate:         20.5509 W[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]    voltage:             11.77 V[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]    time to empty:       1.1 hours[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]    percentage:          90%[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]    capacity:            50.7955%[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]    technology:          lithium-ion[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]  History (charge):[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]    1406043530 90.000 discharging[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]    1406043500 91.000 discharging[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]    1406043440 92.000 discharging[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]  History (rate):[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]    1406043530 20.551 discharging[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]    1406043500 19.980 discharging[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][FONT=verdana, geneva][SIZE=2]    1406043440 19.980 discharging[/SIZE][/FONT][/FONT][/COLOR]
[FONT=verdana, geneva][SIZE=2]
[/SIZE][/FONT]

---

### Post by artm on 2014-07-24
I'm seeing the same numbers on a panp9 model. This has started quite recently, I used to be able to be able to run more than 3 hours on a battery, couple of months ago it became just over 1 hour.

**Update:** I originally misnamed the model, it's panp9, not 6.

$ upower -i /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          BAT0
  vendor:               NOTEBOOK
  model:                BAT
  serial:               0001
  power supply:         yes
  updated:              Thu 24 Jul 2014 16:04:25 CEST (10 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    energy:              13,8861 Wh
    energy-empty:        0 Wh
    energy-full:         18,4371 Wh
    energy-full-design:  48,84 Wh
    energy-rate:         14,1763 W
    voltage:             11,502 V
    time to empty:       58,8 minutes
    percentage:          75%
    capacity:            37,75%
    technology:          lithium-ion
  History (charge):
    1406210635  75,000  discharging
    1406210605  76,000  discharging
  History (rate):
    1406210665  14,176  discharging
    1406210635  14,081  discharging
    1406210605  14,652  discharging
    1406210575  14,652  discharging

---

### Post by untrustytahr on 2014-07-24
Brand new OOTB 2 hours 'normal' use... degrades to 20-30% capacity within 6 months.  On my third battery now (little over a year).  It's one main reason I won't buy another computer from them.

---

### Post by hendrik-0 on 2014-07-30
my gazelle pro battery is at 89% after 9 months, but only because i regularly take it out when the laptop is plugged in. together with the other problems (heat, noisy fan, loose screws that regularly need to be retightened) that also made system76 a no-go for me.

---

