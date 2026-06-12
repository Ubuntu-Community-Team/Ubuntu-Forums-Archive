---
title: "Temperature of the server"
date: 2012-06-21
forum: Server Platforms
---

### Post by Martyguma on 2012-06-21
Hi, I have question. I have at home a fileserver and I would like to check temperatures of my hdds and cpu of this server on my laptop (running on mac OS). Ii there some possible way? I am amater:( I already tried couple things but nothing worked. Thanks

---

### Post by rubylaser on 2012-06-21
Here's how I get my temperatures on my home machine.  I used a combination of smartctl and sensors.  Here's my Bash script.  You'd need to modify this for your scenario.  This only dumps the temps out to the terminal right now, but you could easily modify this to cause a shutdown, or email you if something got too hot.  If you have a multi core machine, this just gets an average temp for each core, so this may not be exactly what you're looking for, but it works fine for my purposes.


```
#!/bin/bash

drives=(sda sdb sdc sdd sde sdf sdg sdh sdi)

temp=""

drivetemp () {
  drive=$1
  printf "drive passed in = %s\n\n" $drive
  temp=`/usr/sbin/smartctl -a -d ata /dev/$drive | grep -m 1 Temperature | awk '{print $10}'`
  return
}

drives_count=${#drives[@]}
index=0
echo CPU temp is "$(sensors | grep Core | cut -f2 -d'+' | cut -f1 -d' ' | awk '{print substr($1,0,3)}' | awk '{ sum+=$1 } END {print sum/NR}')C"
while [ "$index" -lt "$drives_count" ]
do
  drivetemp ${drives[$index]}
  printf "Drive %s temp is %sC\n" ${drives[$index]} $temp
  let "index = $index + 1"
done


```

---

### Post by arrrghhh on 2012-06-21
Hrm, maybe I'm missing something but I can't seem to get that script to work quite right.  I changed the "drives" section to match my system, and that's it.

Here is the output:
```
 sudo ./test
awk: fatal: division by zero attempted
CPU temp is C
drive passed in = sda

Drive sda temp is 43C
drive passed in = sdb

Drive sdb temp is 47C
drive passed in = sdc

Drive sdc temp is 44C
drive passed in = sdd

Drive sdd temp is 42C
drive passed in = sde

Drive sde temp is 37C
```

I had a few stupid user errors, but sorted those out and now I'm not sure what's wrong.  awk appears to be diving by 0?

I do like this script tho.  Webmin doesn't really have a good quick way to glance at temps... For a while I ran conky remotely (so the conky stats were polled from the server and displayed on my workstation) but I have to run Windows now for work... :(

---

### Post by rubylaser on 2012-06-21
Do you have sensors installed? What do you get when you run this?

```
sensors | grep Core
```

It should look something like this.
```
Core 0:      +35.0°C  (high = +86.0°C, crit = +100.0°C)  
Core 0:      +32.0°C  (high = +86.0°C, crit = +100.0°C)  
Core 2:      +31.0°C  (high = +86.0°C, crit = +100.0°C)  
Core 2:      +27.0°C  (high = +86.0°C, crit = +100.0°C)  
Core 1:      +42.0°C  (high = +86.0°C, crit = +100.0°C)  
Core 1:      +33.0°C  (high = +86.0°C, crit = +100.0°C)  
Core 3:      +33.0°C  (high = +86.0°C, crit = +100.0°C)  
Core 3:      +30.0°C  (high = +86.0°C, crit = +100.0°C) 
```

---

### Post by arrrghhh on 2012-06-21
> **rubylaser said:**
> Do you have sensors installed? What do you get when you run this?

```
sensors | grep Core
```

It should look something like this.
```
Core 0:      +35.0°C  (high = +86.0°C, crit = +100.0°C)  
Core 0:      +32.0°C  (high = +86.0°C, crit = +100.0°C)  
Core 2:      +31.0°C  (high = +86.0°C, crit = +100.0°C)  
Core 2:      +27.0°C  (high = +86.0°C, crit = +100.0°C)  
Core 1:      +42.0°C  (high = +86.0°C, crit = +100.0°C)  
Core 1:      +33.0°C  (high = +86.0°C, crit = +100.0°C)  
Core 3:      +33.0°C  (high = +86.0°C, crit = +100.0°C)  
Core 3:      +30.0°C  (high = +86.0°C, crit = +100.0°C) 
```

I do have sensors installed, but your command returns nothing.  Here's the output of simply "sensors":
```
 sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:     +1.23 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:     +3.25 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:       +4.99 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:     +12.09 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:    3245 RPM  (min =  600 RPM)
CHASSIS FAN Speed:1048 RPM  (min =  800 RPM)
CPU Temperature:   +53.0Â°C  (high = +60.0Â°C, crit = +95.0Â°C)
MB Temperature:    +45.0Â°C  (high = +45.0Â°C, crit = +95.0Â°C)
```

Not sure why they look so... weird.  I've never really used sensors before tho, just found it last week ;).

---

### Post by rubylaser on 2012-06-21
You'll need to customize the CPU temperature line to your sensor output.  This "should" get the temp for you.

```
echo CPU temp is "$sensors | grep CPU | cut -f2 -d'+' | cut -f1 -d' ' | cut -f1 -d "." | awk '{print substr($1,0,3)}'"
```

That should give you 53°C based on the output you pasted from sensors :)

---

### Post by arrrghhh on 2012-06-21
> **rubylaser said:**
> You'll need to customize the CPU temperature line to your sensor output.  This "should" get the temp for you.

```
echo CPU temp is "$[color=red]([/color]sensors | grep CPU | cut -f2 -d'+' | cut -f1 -d' ' | cut -f1 -d "." | awk '{print substr($1,0,3)}'[color=red])C[/color]"
```

That should give you 53°C based on the output you pasted from sensors :)

Well, I think I'll quit cluttering this thread, as I really need to learn how to use awk and cut better...

I had to make 2 really simple changes to get it to work, I highlighted those in red.  It's still not quite working, but I'll figure it out - definitely something unique to my setup.

---

### Post by rubylaser on 2012-06-21
> **arrrghhh said:**
> Well, I think I'll quit cluttering this thread, as I really need to learn how to use awk and cut better...

I had to make 2 really simple changes to get it to work, I highlighted those in red.  It's still not quite working, but I'll figure it out - definitely something unique to my setup.

Sorry, I left those out from my original example.  Glad you got it "almost" working :)  Learning to use awk and cut are great things to learn to use (frankly what I provided is ugly and not efficient, but it works).

---

### Post by CharlesA on 2012-06-22
> **arrrghhh said:**
> I do have sensors installed, but your command returns nothing.  Here's the output of simply "sensors":
```
 sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:     +1.23 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:     +3.25 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:       +4.99 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:     +12.09 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:    3245 RPM  (min =  600 RPM)
CHASSIS FAN Speed:1048 RPM  (min =  800 RPM)
**CPU Temperature:   +53.0Â°C  (high = +60.0Â°C, crit = +95.0Â°C)**
MB Temperature:    +45.0Â°C  (high = +45.0Â°C, crit = +95.0Â°C)
```

Not sure why they look so... weird.  I've never really used sensors before tho, just found it last week ;).

That's a bit different from what mine returns, but are you connecting via Putty? Change the encoding to UTF-8 in Window > Translation > Remote character set to get the degree symbol to show up correctly.

Mine reads this:
```
Physical id 0:  +37.0°C  (high = +80.0°C, crit = +98.0°C)
Core 0:         +37.0°C  (high = +80.0°C, crit = +98.0°C)
Core 1:         +37.0°C  (high = +80.0°C, crit = +98.0°C)
Core 2:         +33.0°C  (high = +80.0°C, crit = +98.0°C)
Core 3:         +28.0°C  (high = +80.0°C, crit = +98.0°C)

```

@rubylaser: Nice job with that script. :)

---

### Post by arrrghhh on 2012-06-22
> **CharlesA said:**
> That's a bit different from what mine returns, but are you connecting via Putty? Change the encoding to UTF-8 in Window > Translation > Remote character set to get the degree symbol to show up correctly.

Ah yes, that would explain the funky symbols.

But the machine is multi-core, and it doesn't show all cores?  I guess I don't really care about the individual core temps, but it might be useful.

I probably haven't setup sensors correctly :mad:

---

### Post by CharlesA on 2012-06-22
> **arrrghhh said:**
> Ah yes, that would explain the funky symbols.

I only found out about that recently too. :lolflag:

> But the machine is multi-core, and it doesn't show all cores?  I guess I don't really care about the individual core temps, but it might be useful.

I probably haven't setup sensors correctly :mad:

It shouldn't really need any setup besides running sensors-detect.

Run this:

```
cat /proc/cpuinfo
```

EDIT: I just added this line of code to ~/.bash_aliases:
```
alias cputemp="echo CPU temp is "$(sensors | grep Core | cut -f2 -d'+' | cut -f1 -d' ' | awk '{print substr($1,0,3)}' | awk '{ sum+=$1 } END {print sum/NR}')C""

```

Now I can just run cputemp ;)

---

### Post by rubylaser on 2012-06-22
> **CharlesA said:**
> That's a bit different from what mine returns, but are you connecting via Putty? Change the encoding to UTF-8 in Window > Translation > Remote character set to get the degree symbol to show up correctly.

Mine reads this:
```
Physical id 0:  +37.0°C  (high = +80.0°C, crit = +98.0°C)
Core 0:         +37.0°C  (high = +80.0°C, crit = +98.0°C)
Core 1:         +37.0°C  (high = +80.0°C, crit = +98.0°C)
Core 2:         +33.0°C  (high = +80.0°C, crit = +98.0°C)
Core 3:         +28.0°C  (high = +80.0°C, crit = +98.0°C)

```

@rubylaser: Nice job with that script. :)

Thanks CharlesA :)  Good to know about Putty goofing up the characters.  Luckily, I don't have to work on a Windows box, so I don't have to deal with that.

---

### Post by CharlesA on 2012-06-22
> **rubylaser said:**
> TGood to know about Putty goofing up the characters.  Luckily, I don't have to work on a Windows box, so I don't have to deal with that.

Good thing there. Encoding can be a pain sometimes.

In any case, I like how your script averages the CPU temp. Pretty cool. ;)

---

