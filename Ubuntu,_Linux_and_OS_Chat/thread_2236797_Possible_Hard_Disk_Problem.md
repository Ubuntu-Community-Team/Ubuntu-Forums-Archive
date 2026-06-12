---
title: "Possible Hard Disk Problem"
date: 2014-07-29
forum: Ubuntu, Linux and OS Chat
---

### Post by anon_private on 2014-07-29
I used Disk Utility in Linux (from pendrive) to check my hard drive.

I found. 

One bad sector.
Overall assessment: Disk has a few bad sectors (green button).

Read Error Rate: Good (green button)
Spinup Time: Good (green button)
Start/stop count:N/A

My hard disk looks alright to me.                                                                                                                                


Someone on another board suggested this.


'I've  seen this all before.. I've worked corporate IT, I've worked IT  on a  college campus, and I helped run a computer repair store for 4  years. I  know the signs well. 

  You  said that you've discovered bad sectors on the disk. Modern hard  drives  have a technology called SMART that keeps track of the drive  condition.  Among other things, SMART can remap a small number of bad  sectors,  replacing them with reserved sectors on the disk. If you ever  actually *see*  bad sectors, this means the drive's on-board  software has already  mapped out as many sectors as it can, and you  actually have a  significant problem. Usually, when the bad sector count  starts growing,  it gets worse. This doesn't always happen, but when it  does, this means  you'll corrupt more and more data...'

'So here's a recap:'


  

[LIST]
[*]'Obtain a Linux live DVD (Mint or Ubuntu) or Hiren's Boot Disk. 
[*]Back up your data to a USB hard drive 
[*](optional) Install a new hard drive 
[*]Completely format the drive (NOT a quick format) 
[*]Re-install Windows 
[*]Set up maintenance cycle and scan for bad sectors every day for a week, then once a week' 
[/LIST]



                                                                                                                                    What do you think of this advice - at the re-install stage it could be Linux,

---

### Post by mastablasta on 2014-07-29
why not just set up maintenance cycle and scan for bad sectors. you will soon see if they are growing fast or not. 

this SMART is really unreliable. just had a disk that had problems to boot and was making strange sounds yet all smart tests including deep ones told me "everything is ok, nothing to worry about". and it was still working ok. nothing slow or anything like that. no data being lost...


bought a new, bigger disk and clonezilla'd the old one to the new... I hated the noise and the fact it couldnt' boot properly every time.

---

### Post by tgalati4 on 2014-07-29
Examine the other SMART parameters and print them out.  See if they get worse over time.  SMART only captures about 2/3 of failure modes.  1/3 are not captured and those are the ones to worry about.

Open a terminal:

```
sudo smartctl -a /dev/sda
```

---

### Post by anon_private on 2014-07-29
> **tgalati4 said:**
> Examine the other SMART parameters and print them out.  See if they get worse over time.  SMART only captures about 2/3 of failure modes.  1/3 are not captured and those are the ones to worry about.

Open a terminal:

```
sudo smartctl -a /dev/sda
```

I tried to have a look at this command.

man -k smartctl, but I did not find an entry.

---

### Post by Bucky Ball on 2014-07-29
*Thread moved to **Ubuntu, Linux and OS Chat**.*

If your test shows the green light and 'good' then drive is good, as far as what it was tested for goes. The output from tgalati4's command will prove more enlightening.

> man -k smartctl, but I did not find an entry. 

How do you mean you didn't find an entry? No output? You may need to install smartmontools then try it in a terminal.

From your first post:

> 
Usually, when the bad sector count starts growing, it gets worse. 

You have two bad sectors, from memory, and haven't mentioned anything about checking them again and there was three, so wouldn't be that bothered. Run your test in a week and see if there is more.

---

### Post by stalkingwolf on 2014-08-01
the Hirens disk has a utility called hard drive regenerator.  ir can regen the drive and repair bad sectors.I use it it has saved or extended the life of several for me.

---

