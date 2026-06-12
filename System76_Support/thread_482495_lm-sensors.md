---
title: "lm-sensors"
date: 2007-06-23
forum: System76 Support
---

### Post by voidmage on 2007-06-23
On my Gazelle Performance (gazp3), what do I need to do to enable lm-sensors?
Currently, when I run 'sensors' I get:
```
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

```
The output of sensors-detect is at [http://paste.ubuntu-nl.org/26937/](http://paste.ubuntu-nl.org/26937/)
Output of lsmod is at [http://paste.ubuntu-nl.org/26938/](http://paste.ubuntu-nl.org/26938/)
I also added the modules recommended by sensors-detect. My current /etc/modules is at [http://paste.ubuntu-nl.org/26939/](http://paste.ubuntu-nl.org/26939/)

---

### Post by thomasaaron on 2007-06-23
I tried to load and configure sensors.

The message I got at the end of sensor-detect is the same as yours:
> 
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported.

I don't know much about it, but it looks like it won't work on the Darter or Gazelle.

---

### Post by voidmage on 2007-06-23
I found something that does work:
```
acpi -V
 Battery 1: charged, 100%
     Thermal 1: ok, 58.0 degrees C
  AC Adapter 1: on-line

```
This has an entry with core temperature that I can use.

---

### Post by AusIV4 on 2007-06-24
To check the temperature, I used to use:

```

$ cat /proc/acpi/thermal_zone/THRM/temperature 

```
and get
```

temperature:             53 C

```

However not long ago I installed sensors-applet:

```

sudo aptitude install sensors-applet

```

Added it to my panel, and it gives me updates with the system temperature.

---

### Post by altgrrr on 2007-06-25
I have the same problem, I followed the steps at _[ubuntuguide wiki]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29")_

When finishing the whole thing with  ```
sudo sensors -s
``` I got

```
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

``` :(

---

### Post by thomasaaron on 2007-06-25
Just curious, is there a particular reason you need this utility?

The 'acpi' command provides several useful options for ferreting out system info.

> man acpi

---

### Post by altgrrr on 2007-06-25
acpi only shows cpu-temp ... I'd like to see fan-performance because I have some overheating issues with my laptop :( plus, it's fun too see wierd statistics :D

---

### Post by thomasaaron on 2007-06-25
Why do you think you have overheating issues on your Gazelle Performance?
That's pretty uncommon.

---

