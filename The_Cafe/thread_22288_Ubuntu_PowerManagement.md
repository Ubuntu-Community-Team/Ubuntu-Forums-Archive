---
title: "Ubuntu PowerManagement"
date: 2005-03-26
forum: The Cafe
---

### Post by Leebobs on 2005-03-26
Our computer systems are in-efficient, they guzzle up power... While Ubuntu helps in some ways (by varying CPU speed & voltage, depending on load) there is NO Official energy saving technology.

Are the dev's looking into these projects?
[http://gnomedesktop.org/node/2204](http://gnomedesktop.org/node/2204)
[http://gnome-power.sourceforge.net/](http://gnome-power.sourceforge.net/)

I think it would be great is Ubuntu could help people save energy & the environment... Lets take the lead with this!

---

### Post by jdong on 2005-03-26
The last time I checked (correct me if wrong):

1. Computers don't use that much power (<30W when not in use and idling) anyway, and most consumption is used by the CPU, Video card, and mechanical drives. CPU can be controlled via powernowd (on by default), and mechanical drives can be set to spin down via BIOS or hdparm (not on by default, because it causes undesirable lag and wear)

2. Monitors use the most power (CRT). Replacing CRT's with flat panels help, and GNOME's screen saver system can shut off the monitor when inactive, also.


I think we have that part set. GNOME power manager looks cool, and I definitely want to see it in the next release.

---

### Post by blinksilver on 2005-03-26
he make a good point, but the biggest draw back is the linux kernel, sleep and hibernate just don't work right, you need to be running 2.6.7 or 8 and those method are really old, and recent update have proved good, they have broken alot of the system, the concept is good, but until 2.6.12 starts seeing the limelight it is all just a pipe dream

---

### Post by Leebobs on 2005-03-27
These figures are from PC Pro in the UK:
*High end PC (P4 3Ghz) - Not including monitor - Costs per 5 years (I think), normal use assumes 8hrs a day, five days a week.*
Left running SETI@Home (all the time): £876
Normal Use then S1 Standby: £278
Normal Use then S3 Standby: £132
Normal Use then Turned Off: £115

Normal use then leaving PC always on, but not under any load at all, costs between £300-£400.

So proper power management could save each user £000's over their system lifetime. Not to mention that for each kWh used in the UK 620g of CO2 is release into the atmosphere... 

So each PC using an average of 200W, for 10 hours a day, causes over 1.2Kg of C02 to be released into the atmosphere per day.

Old CRT Screens do use large amounts of money, and TFT's only a fraction:
Taxan Ergovision: £150
Sharp LL172G-B (Modern TFT): £25 (Plus uses less than 1w in stand-by)

So yes, putting you screen into standby after 5 mins really will save you money, but your idle system keeps guzzling it  :cry:

I would love to see anything that can save users money, along with reducing green house gas emissions, as a high priority for Linux! It fits exactly with our philosophy!

---

### Post by jdong on 2005-03-27
3.4GHz's are usually monsters anyway as far as other peripherals go. I don't think many of us here use such systems.


These stats come from a Canadian university, for the average 1.8Ghz P4.

    *  during boot power in watts is close to 110w
    * during idle, no power management,. close to 60w
    * during full power saving, no hard disk spin, machine in sleep mode, 35w


There's still some difference between idle and standby, but either way, it's not that much power wasted.

As far as tradeoffs, constantly spinning down the system and powering it back on is **NOT GOOD** for the computer -- expect it to fail a few years sooner. The last hard drive I did this with, a 10GB Western Digital, it died in 2 years!

---

### Post by Leebobs on 2005-03-27
[QUOTE=jdong]As far as tradeoffs, constantly spinning down the system and powering it back on is **NOT GOOD** for the computer -- expect it to fail a few years sooner. The last hard drive I did this with, a 10GB Western Digital, it died in 2 years![/QUOTE]

I'm not very sure about this, it was described as one of the Myths of Computing as a HDD's idle state and powerdown state are very similar.

But I think this is one of the things we should consider for the Ubuntu future! Maybe with HDD spin down disabled by default (just to be on the safe side).
NB: The only Hard Disks to ever fail on me - Western Digital.

---

### Post by poofyhairguy on 2005-03-27
[QUOTE=Leebobs]Our computer systems are in-efficient, they guzzle up power... While Ubuntu helps in some ways (by varying CPU speed & voltage, depending on load) there is NO Official energy saving technology.[/QUOTE]


Does hitting the power button when I'm not using it count?

;)

Good points by the way....

---

### Post by soboku1 on 2005-04-15
Hi Im now to Ubuntu and Ihave the latest version installed. I would like to no how I can stop my system from going into some kind of power saving mode. The screen goes blank intill I move the mouse. I have no screen savors running nor do I have any settings for power management except for where the batter is and its just for batter no other settings. Does any one no where i turn this off? I am running KDE latest version.


Thanks joey.

---

