---
title: "Server Power Consumption Management"
date: 2008-06-03
forum: Server Platforms
---

### Post by KB1LQC on 2008-06-03
I am in the process of setting up a server and will have it do some other things too in the background.  But for the most part I have a feeling that it will not be accessed more than a few times per day.  I have Ubuntu Server 8.04 running on the PII 256 MB Ram and its going great!

One thing thats always interested me was power management.  If it will not be doing much all the time is there a way to manage whats going on or have certain parts of the computer that are never used turned off?  My goal is to have the computer consume as little power as possible... any suggestions?

---

### Post by Oldsoldier2003 on 2008-06-03
> **KB1LQC said:**
> I am in the process of setting up a server and will have it do some other things too in the background.  But for the most part I have a feeling that it will not be accessed more than a few times per day.  I have Ubuntu Server 8.04 running on the PII 256 MB Ram and its going great!

One thing thats always interested me was power management.  If it will not be doing much all the time is there a way to manage whats going on or have certain parts of the computer that are never used turned off?  My goal is to have the computer consume as little power as possible... any suggestions?

Don't connect a monitor.

---

### Post by rickyjones on 2008-06-03
> **KB1LQC said:**
> I am in the process of setting up a server and will have it do some other things too in the background.  But for the most part I have a feeling that it will not be accessed more than a few times per day.  I have Ubuntu Server 8.04 running on the PII 256 MB Ram and its going great!

One thing thats always interested me was power management.  If it will not be doing much all the time is there a way to manage whats going on or have certain parts of the computer that are never used turned off?  My goal is to have the computer consume as little power as possible... any suggestions?

Install as weak of a power supply as you can while keeping it stable. If you really want to make it energy efficient then I'd recommend spend more up front and get a newer VIA chip. Should be enough power to do what you need to do and it'd use a lot less power than the standard P2.

-Richard

---

### Post by SoundFriend on 2008-06-03
Every little helps. 
Make sure that the hard disk powers down after a period.
You could get the server to shutdown overnight if you don't need it. It may be possible to then use wake-on-LAN to start it up on demand.  

I'd be interested too if someone knows how to do this. :lolflag:

SF

---

### Post by KB1LQC on 2008-06-03
> Every little helps.
Make sure that the hard disk powers down after a period.
You could get the server to shutdown overnight if you don't need it. It may be possible to then use wake-on-LAN to start it up on demand.

I'd be interested too if someone knows how to do this.


Hmmm... this is more along the lines of what I was thinking about, a software approach.  I do not have a monitor attached to it at all and I log into it through SSH and do everything command with my laptop.

Ive played around with "powertop" but im not sure if it would apply to a minimalist ubuntu (server).

---

### Post by mlapaglia on 2008-06-03
Disable any and every service that you don't need.
Have the monitor turn itself off after a set amount of time.
In your BIOS (if applicable):
Turn powerstep on, or any hardware controls for power managment, which will turn your CPU down when it isn't being used.

Depending on the type of computer, have it suspend to S3 or even turn it off during the night or during times of inactivity. Either have it set to wake up at a set time, or issue a Wake-On-LAN command to do it.

Disable any ports on the computer you aren't using, which will free resources (com ports, LPT ports, etc).

If your BIOS supports varying fan speed, enable that, which will turn the fans down when the computer isn't running hot.

Set your hard drive to spin down when it isn't being used, set a larger cache so it isn't accessed as often.

Get as small of a power supply as possible.

Underclocking could be an option.
That's about all I can think of..

---

### Post by KB1LQC on 2008-06-03
> **mlapaglia said:**
> Disable any and every service that you don't need.
Have the monitor turn itself off after a set amount of time.
In your BIOS (if applicable):
Turn powerstep on, or any hardware controls for power managment, which will turn your CPU down when it isn't being used.

Depending on the type of computer, have it suspend to S3 or even turn it off during the night or during times of inactivity. Either have it set to wake up at a set time, or issue a Wake-On-LAN command to do it.

Disable any ports on the computer you aren't using, which will free resources (com ports, LPT ports, etc).

If your BIOS supports varying fan speed, enable that, which will turn the fans down when the computer isn't running hot.

Set your hard drive to spin down when it isn't being used, set a larger cache so it isn't accessed as often.

Get as small of a power supply as possible.

Underclocking could be an option.
That's about all I can think of..

Sounds like a great step in the right direction I am going to check out what I can do!



Bryce
KB1LQC

---

### Post by Beowulf878 on 2008-07-25
As I understand it, its not possible at the moment to turn off hard-drives after a set time in linux because people are concerned about shortening the lifespan of the harddisk: I did find a thread where it was proposed on brainstorm.ubuntu.com (can't find it now, but it is there somewhere). 

I use a Koolu (I like it so much, as the moment I use it for my main pc), which is essentially a SoC with a laptop harddrive and no fan - its a sealed unit. The max operating temperature of the drive is 55 degrees, and it idles at 44, and since it produces a lot of the heat I would like to turn it down as well!

Good luck finding a solution = ;)

---

### Post by /etc/init.d/ on 2008-07-25
> **Beowulf878 said:**
> As I understand it, its not possible at the moment to turn off hard-drives after a set time in linux because people are concerned about shortening the lifespan of the harddisk

It is easily possible, but you rightly say it will measurably decrease the lifespan of the drive if you do it too often.  

A modern hard drive uses between 1 and 4 watts when it is idle.  They are not the power-hungry beasts they used to be.  Saving power is good, but so too is keeping the drive in good shape and thus maximising data integrity.

---

### Post by Beowulf878 on 2008-07-25
> They are not the power-hungry beasts they used to be.

Especially true of the Fujitsu MHW2080AT they have put into my Koolu!

As you corrected me it <is> indeed easily possible (as google told me) by using ```
sudo hdparm
``` - however I am in fact now more worried that the firmware will be aggressively trying to stop my drive at every opportunity.

I also found that ```
sudo smartctl -a /dev/hda
``` gives some information on the state of your hard drive - if its SMART enabled, unless its been upgraded I do not know if the one on your p2 system will be able to use that... that might help you decide whether its worth the risk etc.

If I was a little more skilled I would probably put a crontab script or something up so it could power-down whilst you are out at work or asleep, but unfortunately I am not! 


Good luck!

---

