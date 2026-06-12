---
title: "Whats the power on hours of the hard drive in your main pc?"
date: 2011-03-25
forum: The Cafe
---

### Post by markp1989 on 2011-03-25
was just looking at the disk utility program on my pc and saw that the power on time of the drives in my torrentslaves/htpc is **1.3 years**, considering the drives were brought in February 2010 thats a large percentage of uptime.

the one in my desktop is a ssd and doesnt show a value for powered on

edit: 

added power cycle count


sdb1 (htpc)
Start_Stop_Count  655
Power_On_Hours    11637

sdc1 (htpc)
Start_Stop_Count  673
Power_On_Hours    11142


sda1 (in my laptop drive about 1 week old)
Start_Stop_Count  127
Power_On_Hours    68
edit again: what is "Load_Cycle_Count" ? on my laptop is already at 16,094

---

### Post by CharlesA on 2011-03-25
One of the drives on my Server's RAID array showed 12823 hours. Can't remember when I bought that drive, but it's been a couple years.

edit: Start Stop count and power cycle count were both at 147.

---

### Post by Dustin2128 on 2011-03-25
like, a lot.

---

### Post by tjeremiah on 2011-03-25
1.6 yrs, 4,835 power cycles.

---

### Post by cariboo on 2011-03-25
I've got 2 160Gb drives in this system thet were bought 2 weeks apart in 2006 one has 1.9 yrs on it, and the other has 294 days, they've both been in use the same amount of time.

---

### Post by fela on 2011-03-25
Windows 7 PC:
Hard drive 0: 8697 power-on hours; **2753** start-stops
Hard drive 1: 4974 power-on hours; 1934 start-stops

Debian 5 Server:
Hard drive 0: 1479 power-on hours; 17 start-stops
Hard drive 1: 4205 power-on hours; 494 start-stops

Arch Linux PC:
Hard drive 0: **14848** power-on hours; 561 start-stops

You may see a slight anomaly here. Server's hdd1 used to be an external drive, and arch pc's hdd0 used to be server's hdd0. This explains a) server's hdd1 high start-stop count, b) server's hdd0 low power-on hours count (its hard drive upgrades were done round the beginning of this year as I recall), and c) it also explains arch pc's high power-on hours count [used to be server's drive, on 24/7].

---

### Post by markp1989 on 2011-03-25
> **fela said:**
> Windows 7 PC:
Hard drive 0: 8697 power-on hours; **2753** start-stops
Hard drive 1: 4974 power-on hours; 1934 start-stops

Debian 5 Server:
Hard drive 0: 1479 power-on hours; 17 start-stops
Hard drive 1: 4205 power-on hours; 494 start-stops

Arch Linux PC:
Hard drive 0: **14848** power-on hours; 561 start-stops

You may see a slight anomaly here. Server's hdd1 used to be an external drive, and arch pc's hdd0 used to be server's hdd0. This explains a) server's hdd1 high start-stop count, b) server's hdd0 low power-on hours count (its hard drive upgrades were done round the beginning of this year as I recall), and c) it also explains arch pc's high power-on hours count [used to be server's drive, on 24/7].

thats interesting shows how the usage patterns change the way this disk wears 


gonna look at my laptop in a minute and see how it compares, drive is only a week old

edit: laptop drive
sda1 (in my laptop drive about 1 week old)
Start_Stop_Count 127
Power_On_Hours 68

i added some more info about my drives on the OP

---

### Post by fela on 2011-03-25
> **markp1989 said:**
> thats interesting shows how the usage patterns change the way this disk wears

Well looking at my results closely, it's obvious that something's up with the server and arch PC...the first one's fairly normal for a desktop.

> Start_Stop_Count 127
Power_On_Hours 68

Assuming you've had your laptop for a week, it's been on about 10 hours each day, but the HDD spins down every half an hour or so. Either you're putting the laptop away all the time, or the software (OS) sleeps the drive automatically (Windows/Mac/Ubuntu all do by default I'm pretty sure).

I guess that's a pretty normal result then...

---

### Post by cgroza on 2011-03-25
Mine says 2.6 years. It is a pretty old HDD.

---

### Post by Dustin2128 on 2011-03-25
> **cgroza said:**
> Mine says 2.6 years. It is a pretty old HDD.
Not that old, I've got some 15 year old hard drives that are still ticking. Oh...

---

### Post by TuxLyn on 2011-03-25
The easiest way to check how long your hard drive been running is going to System -> Administration -> Disk Utility under Ubuntu Gnome desktop.

My longest run hard drive is 2.4 years. Which is Western Digital 250 GB @ 7200RPM with 2MB cache. Haven't had any issue with it yet. Using it for my Ubuntu 10.10 install and for any future versions.

---

### Post by wojox on 2011-03-25
2005 Compaq Presario Media Center:

Power-on Hours - 3.5 years

Start/Stop - 2166

---

### Post by Ocxic on 2011-03-25
3.6 years

---

### Post by emanuel.landeholm on 2011-03-26
[LIST]
[*]548 cycles 323 days (ubuntu root disk, 500 GB)
[*]1010 cycles 146 days (windows xp, 160 GB)
[*]918 cycles 2.0 years days (my oldest usable disk, 320 GB)
[*]44 cycles (?) 1.3 years (backup, media 1000 GB)
[/LIST]

---

### Post by NightwishFan on 2011-03-26
My laptop: 283.3 days.

---

