---
title: "Kubuntu 9.10; Its still beta, but do you think its ready?"
date: 2009-10-12
forum: The Cafe
---

### Post by Exodist on 2009-10-12
Hey Everyone,
I ordered a new hard drive for my /home directory and its coming in sooner then I expected. Do you guys think Kubuntu 9.10 is ready for a main desktop. I have had hardly no issues with it running as a live CD. Also with my crazy drive hierarchy I didnt want to reinstall in 2 weeks.

I got 2x 74GB WD Raptors that will be running RAID0 and then a 320GB Cavier that will be my /home directory..


Cheers,
Exo

---

### Post by NormanFLinux on 2009-10-12
The Kubuntu Netbook Edition 9.10 beta is ready. There have been updates twice a day since it came out. It should be ready when the general release is available later this month.

---

### Post by Rogue dog on 2009-10-12
Kubuntu Karmic is Beta, that generally means not ready.

One thing at this moment is a number of people not being able to update via gui.

this command solves this beta issue

```
sudo aptitude update && sudo aptitude dist-upgrade
```

---

### Post by Warpnow on 2009-10-12
I believe you'll have to run a normal sudo aptitude upgrade as well as the dist-upgrade to be fully up to date. Could be wrong, don't really pay attention, heh. Have a script that runs those commands and a few others.

---

### Post by cookiecruncher on 2009-10-12
I get errors on bootup. I wouldn't call it stable/reliable yet. (kwin, apport, etc.)

oops, just rebooted and NO errors. :mad: Maybe the latest update fixed them?
```
Linux kubuntu910 2.6.31-13-generic #44-Ubuntu SMP Sat Oct 10 15:27:55 UTC 2009 i686 GNU/Linux
```

```
One thing at this moment is a number of people not being able to update via gui.
```
Any alternatives for a GUI? Adept?

---

### Post by K.Mandla on 2009-10-12
> **Exodist said:**
> Do you guys think Kubuntu 9.10 is ready for a main desktop.
If you have to ask, then my answer is no.

Sorry to be blunt, but beta software is beta software. If you're not prepared to fix something or suffer the possibility of breakage, then you shouldn't be using it.

Be patient, wait a couple of weeks, go through the installation and you'll have peace of mind.

---

### Post by Grimhound on 2009-10-12
The 9.10 beta currently:
-Does not operate CDs or DVDs with the included software, even when restricted extras are in place. Media players that rely on the system itself (everything but VLC, which runs self-contained) cannot currently read the CDDA format (music CDs).
-Is still being built. Included IM client, Empathy, lacks sound files.  Design decisions are still being made even this close to the release.
-Has some really annoying issues with PulseAudio, yet that's nothing surprising.

---

### Post by madjr on 2009-10-12
i would stick with jaunty n upgrade to kde4.3.2

then wait for final karmic and upgrade. Since you have latest kde, the upgrade should be faster

since i use gnome and kde, i will dl the normal ubuntu and then install kubuntu-desktop just for safety

---

### Post by Exodist on 2009-10-13
> **K.Mandla said:**
> If you have to ask, then my answer is no.

Sorry to be blunt, but beta software is beta software. If you're not prepared to fix something or suffer the possibility of breakage, then you shouldn't be using it.

Be patient, wait a couple of weeks, go through the installation and you'll have peace of mind.


The reason I asked was due to the fact I had only seen one issue with it in regards to KDEs compositing engine and that was said to been fixed a few patches ago.

So I asked to see if there was any issues that may had/will arise if I went ahead and installed the beta. 

The reason that prompted me to ask is I got a new hard drive arriving tomarrow to replace my current hard drive which is set as my /home directory. In addition I was going to put both my 74GB raptor drives back to RAID0.  So this isnt a easy single hard drive install. Normally this install is fairly easy, but if the distro has installer bugs it can be a pain.

---

### Post by TheNessus on 2009-10-13
do not install Karmic yet. I've got a lot of issues with it, and currently resorted to using damned Vista again.

I have issues with loading Karmic after booting when I set it to use the Nvidia 185. driver. When I did a full system upgrade it failed to load GRUB correctly... etc. it is not stable - BUT - without upgrading or using the driver, it is very stable and very smooth and is amazing. Can't wait for the release.

---

### Post by Exodist on 2009-10-13
I am currently downloading the alternate cd of kubuntu jaunty. I may just wait till LTS to upgrade again. I got KDE 4.2.2 installed right now and it appears very stable to use.

---

### Post by markbuntu on 2009-10-13
There are still a lot of serious updates going on so no, not quite ready. If you can install it in its own partition then go ahead but if you have multiple distros you might have some problems with grub2 if you put it on the MBR.

People have been complaining about it not seeing there windows installs and it is unable to boot from one logical partition to another so make sure you put grub2 on a primary partition. Or you can put grub2 on your primary or logical karmic partition and chainload to it from your existing grub. That is what I do.

---

### Post by Exodist on 2009-10-15
Sounds like Grub2 needs deferred until 10.10. I would say until 10.04, but that ones a LTS and want only most stable software in it.

---

