---
title: "snmp &amp; lm-sensors - can it work?"
date: 2006-07-25
forum: Server Platforms
---

### Post by dyonisius1973 on 2006-07-25
Hi guys

I've set-up a Dapper server and am using the SNMP utilities to monitor stuff like disk/cpu/mem usage.
I have installed the lm-sensors packages and now I'm able to see all kinds of hardware info.
What I would like to do is combine these, so that I can use SNMP to monitor fan speeds, temperatures etc.
My lm-sensors work (i get nice info with the **sensors **command). And my SNMP also works.
There is a lot of output from **snmpwalk -c public -v1 localhost**, but no sign of lm-sensors.

Anyone an idea how to get this going?

FYI, I have just switched from Debian/Sarge to Ubuntu/Dapper to get rid of self-compiling packages. I hope it is not neccessary in this case...

---

### Post by barti on 2006-09-03
Don't know if anyone has this working, but I'd like to do the same. There's a MIB file named 'LM-SENSORS-MIB.txt' in '/usr/share/snmp/mibs/' - is there anything that needs to be done to persuade snmpd to see the sensor data?

Steve

---

### Post by tflanders on 2006-11-06
I do this with MRTG and LM Sensors. Take a look [http://www.networkpulse.com/mrtg/system-analysis/](http://www.networkpulse.com/mrtg/system-analysis/)

I have sample mrtg configs here [http://raven.networkpulse.com/mrtg_content/index.html](http://raven.networkpulse.com/mrtg_content/index.html)

This is an external script I call from within MRTG config to graph cpu temp.

Shell Script

#!/bin/sh
IN="`/usr/bin/sensors -f | grep 'CPU Temp' | cut -f2 -d"+" | cut -f1 -d '.'`"
#"`/usr/bin/sensors -f | grep 'M/B Temp' | cut -f2 -d"+" | cut -f1 -d"°"`"
OUT=250
echo $IN
echo $OUT


MRTG File
#
# CPU Temperature
#
Target[cpu.temp]: **`/home/mrtg/cfg/cpu_temp.sh**`
MaxBytes[cpu.temp]: 250
Options[cpu.temp]: growright,gauge,nopercent
Title[cpu.temp]: CPU Temperature
PageTop[cpu.temp]: <H1>CPU Temperature</H1>
WithPeak[cpu.temp]: dwmy
YLegend[cpu.temp]: Temperature
ShortLegend[cpu.temp]: Fahrenheit
LegendI[cpu.temp]: &nbsp;Temp:
LegendO[cpu.temp]:

---

