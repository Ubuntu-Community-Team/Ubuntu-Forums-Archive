---
title: "bandwidth counter"
date: 2008-04-15
forum: The Cafe
---

### Post by t4coffee on 2008-04-15
hi, 

i'm writing a bash script that does a grep on ifconfig eth0 to filter my RX and TX values to an external file.  i was wondering if this was the most accurate way of doing it AND if there was a way to schedule the script to run right before shutdown (cron wouldn't be able to do it right??)

also is there an app i could just install to keep track of how much upload/download traffic i consume?

much appreciated, 
t4coffee

---

### Post by loell on 2008-04-15
the system monitor has it  already , in the resource tab. :)

---

### Post by notwen on 2008-04-15
Check synaptic for any of the following:

bmon
bwm
bwm-ng
cbm
iftop
ipfm
pktstat
speedometer

---

### Post by Dr Small on 2008-04-15
I wrote a usage meter script in bash:
```
#!/bin/bash

#PLEASE CHANGE THIS
#Interface:
interface="ath0"


#BEGIN
download=`ifconfig $interface | grep bytes | awk '/RX/ {print $2}' | sed 's/bytes://'`
start=$(($download / 1048576))
startkb=$(($download / 1024))
time=`date +%s`


while true;do clear;
download2=`ifconfig $interface | grep bytes | awk '/RX/ {print $2}' | sed 's/bytes://'`
start2=$(($download2 / 1048576))
startkb2=$(($download2 / 1024))
current=$(($start2 - $start))
currentkb=$(($startkb2 - $startkb))
currentbytes=$(($download2 - $download))
time2=`date +%s`
totaltime=$(($time2 - $time))
timeminutes=$(($totaltime / 60))
timehours=$((timeminutes / 60))

echo "Current Download Usage:"
echo 
echo $current MBs         
echo $currentkb KBs
echo $currentbytes Bytes
echo 
echo
echo "Elapsed Time:"
echo 
echo $timehours hours
echo $timeminutes minutes
echo $totaltime seconds
echo 

sleep 1;

done

```

You could modify it to your needs, though.

---

### Post by t4coffee on 2008-04-15
> **loell said:**
> the system monitor has it  already , in the resource tab. :)

well would you look at that!! it's there! ahah

Dr. Small: that's impressive. it's exactly what i had in mind. but i was thinking you wouldn't need the "start" values since they'd be 0 (zero) initially. hehe i liked the usage time calculations tho :) cheers man!

notwen: thanks for suggesting iftop. it seems to be the best one to suite my needs. thanks!!

---

### Post by Dr Small on 2008-04-15
The start variables were simply used to find the total (to begin with) and have something to divide and subtract against :)

---

