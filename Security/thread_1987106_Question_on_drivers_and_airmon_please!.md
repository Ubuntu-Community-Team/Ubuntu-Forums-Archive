---
title: "Question on drivers and airmon please!"
date: 2012-05-25
forum: Security
---

### Post by listerdl on 2012-05-25
I am playing around with airmon-ng - quick question if anyone knows the answer to this please - 

When I start airmon-ng in a terminal I get two drivers.

Is that bad practice to keep both alive? It just feels better to kill one of them off? (In my case not rtl8187 - which is preferred chipset I have).

How do I kill off the other driver that is not required? (Do I need to bother?)

Thanks!

---

### Post by kevdog on 2012-05-26
2 drivers?  Need more specifics?  Are you sure you are not just placing your current driver in Monitor Mode?

---

### Post by listerdl on 2012-05-26
Thanks - 

When I give the command "airmon-ng" I only get one driver - the Intel one listed below. 

I then activate the rtl8187 driver using "modprobe rtl8187" so there are two drivers now.

Should I - and how do I - kill the Intel driver please? Thanks!!

*airmon-ng*


*Interface	Chipset		Driver*

wlan0		Intel 4965/5xxx	iwlagn - [phy0]
wlan1		RTL8187 	rtl8187 - [phy1]

---

### Post by jon zendatta on 2012-05-26
Do you mean to kill a process? [http://www.cyberciti.biz/faq/kill-process-in-linux-or-terminate-a-process-in-unix-or-linux-systems/]("http://www.cyberciti.biz/faq/kill-process-in-linux-or-terminate-a-process-in-unix-or-linux-systems/")
or:
Sometimes when you start airmon-ng, more than 1 interface shows up, like ath0,ath1,ath2 etc. Stop them first:
```
airmon-ng stop ath1
```
:KS

---

### Post by listerdl on 2012-05-26
Thanks! So you suggest that it is better to have just ONE driver activated?

---

### Post by jon zendatta on 2012-05-26
Yes thats right. You only have the one wireless driver, so thats the driver you put in monitor mode. To identify which wireless interface to use:
```
iwconfig
```
 Extra processes start when you airmon-ng start, kill these, otherwise these pids become problematic for aireplay-ng & airodump-ng.:KS

---

### Post by listerdl on 2012-05-26
> **jon zendatta said:**
>  Extra processes start when you airmon-ng start, kill these, otherwise these pids become problematic for aireplay-ng & airodump-ng.:KS

Thanks - you are really helpful. 

- So, you reckon it is better to kill the driver I dont want BEFORE I start airmon-ng?

- i.e. if I don't want this driver (Intel 4965/5xxx iwlagn - [phy0]) - AND - if this is located on the interface [COLOR="Red"]wlan0[/COLOR] then BEFORE starting airmon-ng I do this:

```
airmon-ng stop [COLOR="Red"]wlan0[/COLOR]
```

Would that be correct?

-- also --

how come you are referring to "ath" - ?

My basic read is that anything "ath" refers to devices that are parts made by Athero?

I guess my question is that I should kill the driver using whichever [COLOR="Red"]wlan[/COLOR] I dont want it on?

THANKS!

---

### Post by jon zendatta on 2012-05-26
Hi Listerdl, sorry for slow reply. I was just giving ath0 as an example. I use mon0 for airmon-ng.
You start airmon-ng then remove the interface you do Not require. This is the interface that is not in monitor mode.
Thats the best I can explain it.:KS

[B]sudo airmon-ng start <interface>

sudo airmon-ng stop <interface not in monitor mode>[/B]

Use **iwconfig** to check you status

---

### Post by cariboo on 2012-05-27
As aircrack/airmon is no longer in the repositories, we no longer support these programs. Please go to the [Backtrack Forums]("http://www.backtrack-linux.org/forums/forum.php") for support. Thread Closed.

---

