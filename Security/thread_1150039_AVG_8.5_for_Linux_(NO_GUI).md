---
title: "AVG 8.5 for Linux (NO GUI)"
date: 2009-05-05
forum: Security
---

### Post by 67GTA on 2009-05-05
I just downloaded the newest AVG for Linux (8.5). It works fine. I thought I would save a lot of users the trouble and tell you that it is command line only. There is no user interface for AVG 8.5.

[http://free.avg.com/download](http://free.avg.com/download)

---

### Post by Vostrocity on 2009-05-05
I'm pretty sure I see a thumbnail of a GUI on the download page.. :confused:

---

### Post by lovinglinux on 2009-05-06
I'm currently using Bitdefender and it works like a charm. It has a nice interface, a drop-box and nautilus integration (this one crashing in Jaunty). It is also pretty fast. See the discussion [here](http://ubuntuforums.org/showthread.php?t=1130400) (including instructions on how to get the download and license key).

---

### Post by tubbygweilo on 2009-05-06
The downloadable instruction [manual]("http://www.avg.com/filedir/doc/LINUX_GROUP/AVG_Free_for_Linux/avg_afl_uma_en_75_2.pdf") illustrates a gui, might be worth a read before deciding to use the product or not.

---

### Post by lunixntu on 2009-05-06
Hi,

I have installed the previous version 7.5 on my ubuntu 8.04 it's work fine, but I have view a new version an then I install the 8.5. The GUI no found.

How do you configure via command line update, folders, schedule and so on ? the manual into site of agv it's a older version.

Tanks you for any suggestions.

lunixntu

---

### Post by lance bermudez on 2009-05-13
I had to use
sudo avgct1 --start to make it work as in to turn it on

for updating(I recommend setting them as an alias)
sudo avgupdate --priority 2

sudo avgupdate -p 3

sudo avgupdate -p 4

for scaning
avgscan -H /home/lance

avgscan --heur /

I have had some dealings with avast so for those of you that need a gui I recommend them.

---

### Post by Sir Jasper on 2009-05-13
Hi,

If  someone is so kind as to answer my questions, which I hope is sufficiently related, please also tell me if I am out of line.

AVG 8.5 (Windows version) cannot be used on my W98SE. However, as Wine is not an emulator could I set Wine to say, XP and use it, or could I just use it leaving my Wine setting at W98?

I agree about Avast and its excellent detection rate. The on-demand Debian scanner seems very quick (although the daily signature update is full, as against incremental, thus not as good for dial-up users) It has a GUI and is easy to install. On-demand it could be used to supplement AVG 8.5.

My regards

---

### Post by lisati on 2009-05-14
Thanks for bringing the new Linux-friendly version to our attention. I haven't looked into it yet, but with 7.5 a lot of people missed the instruction in the documentation to add your Linux account to the AVG user group before updating the documentation. See [here]("http://ubuntuforums.org/showthread.php?t=889552") for more information.

There is a Linux-friendly version of AVG8.5 at [http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl)

I can't use 8.5 on my Win98SE machine either. The only Windows-friendly version I could find in my software library (somewhere around v7.0) works fine until I update the definitions, at which point the system tends to hang...

---

### Post by lance bermudez on 2009-05-14
lisati and Sir Jasper 
at [http://www.avast.com/eng/avast-for-linux-workstation.html](http://www.avast.com/eng/avast-for-linux-workstation.html)

it says

avast! Linux Home Edition

avast! Linux Home Edition represents an antivirus solution for the increasingly popular Linux platform. The Home Edition is offered free of charge but only for home, non-commercial use. Both of these conditions should be met. 

Institutions (even non-commercial ones) are not licensed to use avast! Linux Home Edition.

Avast also has a windows side that may work on your windows box. However avast has a gui for both the windows and linux side.

click here [http://files.avast.com/files/linux/avast4workstation_1.3.0-2_i386.deb](http://files.avast.com/files/linux/avast4workstation_1.3.0-2_i386.deb) to download avst for .deb

to install cd the command line to where you have the file then type
sudo dpkg avast4*.deb

---

### Post by Salpiche on 2009-05-21
> **lance bermudez said:**
> lisati and Sir Jasper 
at [http://www.avast.com/eng/avast-for-linux-workstation.html](http://www.avast.com/eng/avast-for-linux-workstation.html)

it says

avast! Linux Home Edition

avast! Linux Home Edition represents an antivirus solution for the increasingly popular Linux platform. The Home Edition is offered free of charge but only for home, non-commercial use. Both of these conditions should be met. 

Institutions (even non-commercial ones) are not licensed to use avast! Linux Home Edition.

Avast also has a windows side that may work on your windows box. However avast has a gui for both the windows and linux side.

click here [http://files.avast.com/files/linux/avast4workstation_1.3.0-2_i386.deb](http://files.avast.com/files/linux/avast4workstation_1.3.0-2_i386.deb) to download avst for .deb

to install cd the command line to where you have the file then type
sudo dpkg avast4*.deb

I installed Avast a few days ago and every time I enter the registration key it gives me an error stating that there was an error in avast engine, VPS file was destroyed... and I can't find anything about it @ their website other than alot of other people having the same issue.

---

### Post by Richardcavell on 2009-05-27
I just installed AVG and it seems to crash if I let it scan my hard disk for about 15 minutes.

I am running it with sudo, since without sudo it cannot access certain directories.  Is this the right thing to do?  I suspect that sudo is timing out and it's losing its privileges.

When it crashes, my Macbook just suddenly turns off.  No warning, no log file, no shutdown sequence, just *puff* and the screen is black.

Richard

---

### Post by jrusso2 on 2009-05-28
Actually i was a bit peeved when it had no GUI.  But now I like it cause its really fast.  Scans the same partition in half the time as the GUI version.

---

### Post by HereInOz on 2009-05-30
Just a little curious.  Avgscan did find a virus in a group of files on which I tested it.  I knew the virus was there, so I was not surprised, but at the end of the scan it just said, yep, there is a virus there, and it left it there.

Anyone got any ideas how to make it delete the virus, or quarantine it, or something along those lines?  I will keep looking, but up to now I haven't been able to find a way to tell it to get rid of the virus(es) it finds.

Any clues would be appreciated.

---

### Post by lovinglinux on 2009-05-30
> **HereInOz said:**
> Just a little curious.  Avgscan did find a virus in a group of files on which I tested it.  I knew the virus was there, so I was not surprised, but at the end of the scan it just said, yep, there is a virus there, and it left it there.

Anyone got any ideas how to make it delete the virus, or quarantine it, or something along those lines?  I will keep looking, but up to now I haven't been able to find a way to tell it to get rid of the virus(es) it finds.

Any clues would be appreciated.

As far as I know, that's all it does. So I recommend using [BitDefender](https://help.ubuntu.com/community/BitDefender), which can put the files in quarantine or delete them. It also has a nice gui and scans fast.

---

### Post by Chino355 on 2009-06-13
So what the hell!? can avg 8.5 be installed or what? :-s

---

### Post by cariboo on 2009-06-13
If you had read the whole thread, the answer is yes, but there is no gui.

---

### Post by ddrichardson on 2009-06-13
> **lance bermudez said:**
> I had to use
sudo avgct1 --start to make it work as in to turn it on

for updating(I recommend setting them as an alias)
sudo avgupdate --priority 2

sudo avgupdate -p 3

sudo avgupdate -p 4

for scaning
avgscan -H /home/lance

avgscan --heur /

I have had some dealings with avast so for those of you that need a gui I recommend them.
I haven't used this in a while but rather than using sudo for the updates, I understood you could add users to the avg group.

---

### Post by Norwal on 2009-09-16
I like AVG on my Windows box but with out GUI it's of no value to me.  I'm trying BitDefender and so far it working great.

---

### Post by cariboo on 2009-09-16
I find the latest Windows versin of AVG is getting pretty annoying with the added toolbars and IE8 add-ons.

---

### Post by lance bermudez on 2009-09-17
How would you add users to the avg group?

---

### Post by cariboo on 2009-09-17
To add someone to the avg group open a terminal and typ:

```
sudo gpasswd -a <user> <group>
```

Where <user> = the user and <group> = the group

---

### Post by lance bermudez on 2009-09-18
i did
sudo gpasswd -a lance avg

now i get /usr/bin/avgupdate: 17: /opt/avg/avg8/bin/avgupdate: Permission denined

when i do avgupdate -p 4

what am i doing wrong?

---

### Post by phillw on 2009-09-18
Not wishing to throw a 'hand-grenade' into the discussion, but, IMHO get rid of AVG - there is a tutorial for it, it's a pain to shift - a bit like ridding a windoze machine of Norton.

For all windoze users AVG is my 1st choice of AntiVirus to use. It just seems that their *nix version is a bit of an after thought :-(

Phill.

---

### Post by deanhanson on 2009-09-19
Hi...
 Hey Buddy thanks for sharing the post because i am thinking of to download one anti virus for my linux server but from here i find such a nice view regarding AVG.... Thanks for sharing the post...

---

### Post by johnh10000 on 2009-11-18
Hi folks

on demand with avast!  How does one turn it on?

> **Sir Jasper said:**
> Hi,

If  someone is so kind as to answer my questions, which I hope is sufficiently related, please also tell me if I am out of line.

AVG 8.5 (Windows version) cannot be used on my W98SE. However, as Wine is not an emulator could I set Wine to say, XP and use it, or could I just use it leaving my Wine setting at W98?

I agree about Avast and its excellent detection rate. The on-demand Debian scanner seems very quick (although the daily signature update is full, as against incremental, thus not as good for dial-up users) It has a GUI and is easy to install. On-demand it could be used to supplement AVG 8.5.

My regards

---

### Post by lance bermudez on 2009-11-18
I installed the deb of avast from the avast web cite and in my menus i have a blue ciricle with a white A in it. Click that to open avast. Also i think it is avast in the command line with avast-update to update from the command line. You can also update avast when you open it from the menus

---

### Post by TechZilla on 2011-05-15
I know i'm digging this one up but...,

"AVG ANTI-VIRUS FREE EDITION FOR LINUX"
8.5 has no GUI, which i actually prefer

7.1, 7.X did have a GUI, it was actually really great compared to most commercial Linux GUI offerings.

I personally think the best way to approach the situation would be to offer an "optional" GUI package.

but either way, i prefer the commandline and really like the new avg for Linux.  Unfortunately because our beloved GPL clamAV is horrific. I don't "need" all the bells and whistles..just a QUALITY scanning engine (high performance and effective).  clamAV is SLOW SLOW SLOW! Has a good amount of false negatives, and poor/none heuristics.

---

