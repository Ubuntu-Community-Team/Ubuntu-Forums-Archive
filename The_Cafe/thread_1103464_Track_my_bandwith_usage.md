---
title: "Track my bandwith usage?"
date: 2009-03-22
forum: The Cafe
---

### Post by linuxisevolution on 2009-03-22
I am scared that I might be using more than what comcast wants me too. I setup apachetop on my server and saw that today it reached 22gb. Yikes. And that is mainly just because of my new distribution I'm working on(the iso of course).

Is there an app that can track this? My router tells me in real time but does not keep track.

Thanks!

---

### Post by Dr Small on 2009-03-22
```
ifconfig ath0 | grep bytes
```
Of course, that is nothing sophisticated, but it works. If you have something better, let me know. :)

Also, for "live" tracking of it:
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
You can run that in screen and watch it over a period of time :)

---

### Post by Mehall on 2009-03-22
You can get Conky to show it too!

---

### Post by linuxisevolution on 2009-03-22
I'm not sure that the first option is accurate...
```

debian:~# ifconfig eth0 | grep bytes
          RX bytes:2114087871 (1.9 GiB)  TX bytes:367833192 (350.7 MiB)


```

Or is apachetop wrong?

---

### Post by linuxisevolution on 2009-03-22
> **Mehall said:**
> You can get Conky to show it too!

The server is headless. ;)

---

### Post by linuxisevolution on 2009-03-22
> **Dr Small said:**
> ```
ifconfig ath0 | grep bytes
```
Of course, that is nothing sophisticated, but it works. If you have something better, let me know. :)

Also, for "live" tracking of it:
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
You can run that in screen and watch it over a period of time :)

Thanks! That code is working, but since I am using it over ssh every time it reloads it adds the bandwith that it itself is using, making the reading inaccurate. Is there a way to fix that?

---

### Post by Mehall on 2009-03-22
> **linuxisevolution said:**
> The server is headless. ;)

run it windowed via x11 forwarding? idk =[

---

### Post by linuxisevolution on 2009-03-22
> **Mehall said:**
> run it windowed via x11 forwarding? idk =[

That would take to much resources. It only has a 550mhz cpu and 256mb ram. Using 33mb ram now though.

Conky is just a huge bash script to me.

---

### Post by Mehall on 2009-03-22
> **linuxisevolution said:**
> That would take to much resources. It only has a 550mhz cpu and 256mb ram. Using 33mb ram now though.

Conky is just a huge bash script to me.

To clear things up, I wasn't honestly suggesting x11-ing Conky, lol.

I like Conky on my desktop, and install it whenever I'm using a GUI (okay, I use Crunchbang, so it comes pre-installed :P) but yah, erm.... I have no idea, lol.

you could always do a wget of the routers stats and store it in a file somewhere.

EDIT: again, daft idea and impractical.

---

### Post by smartboyathome on 2009-03-22
If you are behind a WRT router, there is always DD-WRT. It will track all your bandwidth usage for you.

---

### Post by linuxisevolution on 2009-03-22
> **Mehall said:**
> To clear things up, I wasn't honestly suggesting x11-ing Conky, lol.

I like Conky on my desktop, and install it whenever I'm using a GUI (okay, I use Crunchbang, so it comes pre-installed :P) but yah, erm.... I have no idea, lol.

you could always do a wget of the routers stats and store it in a file somewhere.

EDIT: again, daft idea and impractical.

Actually the wget idea is very practical. Thanks for the idea.

But now heres my problem:

I have added my RX and TX data and I find that just me and my server have send around 4gb of data and received 3gb -since they haven't been turned off. 

The problem is if I run the ifconfig $interface | grep bytes command on each interface that ifconfig shows on the router none of the interfaces seem to show the total :(

Should br0, br0:0, eth0, eth1, vlan0, and vlan1 all be added together, or am I missing something?

---

### Post by linuxisevolution on 2009-03-22
> **smartboyathome said:**
> If you are behind a WRT router, there is always DD-WRT. It will track all your bandwidth usage for you.

I am using dd-wrt. I don't know how to view total bandwith usage with it though.

---

### Post by smartboyathome on 2009-04-07
> **linuxisevolution said:**
> I am using dd-wrt. I don't know how to view total bandwith usage with it though.

Sorry for the late reply. To view the total bandwidth usage, go to 192.168.1.1, and then browse to Status > WAN.

---

