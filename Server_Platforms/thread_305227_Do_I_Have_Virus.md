---
title: "Do I Have Virus?"
date: 2006-11-23
forum: Server Platforms
---

### Post by ebozzz on 2006-11-23
I'm still pretty new to Ubuntu and Linux. Just on a whim I decided to install Virus Scanner from Add/Remove Applications. I initiated a scan and to my surprise realized that I could scan my Windows XP partition. I figure what the heck so I go for it. 

Multiple files were detected as being infected with either the W32.Magistr.a@MM or with W32.Netsky.c@MM. I would not allow me to quarantine the files but I did have an option of deleting them. I started to feel a little unsure and decided to boot XP with the purpose of performing a scan. No infected files were detected. What gives? Do I have a virus or not? Is the *Virus Scanner* application reliable? :-k :confused:

---

### Post by insub2 on 2006-11-23
I did a google search for those file names and they appear to be viruses (worms, to be specific).  If these files are on your windows partition, then you have a virus.  I'd say that the problem is that your windows based virus scan is not up to date enough to know that W32.Magistr.a@MM and W32.Netsky.c@MM are viruses.

---

### Post by Circus-Killer on 2006-11-23
personally, i find linux-based virus scanners to be unreliable, with a lot of false-positives. just my experience.

---

### Post by ebozzz on 2006-11-23
> **insub2 said:**
> I did a google search for those file names and they appear to be viruses (worms, to be specific).  If these files are on your windows partition, then you have a virus.  I'd say that the problem is that your windows based virus scan is not up to date enough to know that W32.Magistr.a@MM and W32.Netsky.c@MM are viruses.

The engine/DAT files are up to date and also were current at the time that I performed the scan. If for no other reason, I usually boot into Windows just to get the updates several times a week.

---

### Post by ebozzz on 2006-11-23
> **Circus-Killer said:**
> personally, i find linux-based virus scanners to be unreliable, with a lot of false-positives. just my experience.

That makes me feel better. Which scanners have you tried?

---

### Post by tturrisi on 2006-11-23
What may have happened is the linux av app scanned the already quarentined windows files.  Boot to win, remove any quarantined files from antispyware apps & av apps.  For example, adaware has a dir w/ quarantined files, as does avg av & others.  Once done, boot to linux & rescan.

---

### Post by janbockaert on 2006-11-23
if you use avast anti-virus (its free), you can scan your hard disk before windows boot. I believe that is the only safe way to scan for viruses on windows. If you scan with windows already running, chances are, the virus is clever enough to hide for the virusscanner.

I have no experience with linux-virusscanners, there are no linux-viruses out in the wild. Installing a virus scanner is something you don't have to do anymore in linux.

---

### Post by ebozzz on 2006-11-23
> **tturrisi said:**
> What may have happened is the linux av app scanned the already quarentined windows files.  Boot to win, remove any quarantined files from antispyware apps & av apps.  For example, adaware has a dir w/ quarantined files, as does avg av & others.  Once done, boot to linux & rescan.


I'll try that. Thanks!

---

### Post by ebozzz on 2006-11-23
> **janbockaert said:**
> if you use avast anti-virus (its free), you can scan your hard disk before windows boot. I believe that is the only safe way to scan for viruses on windows. If you scan with windows already running, chances are, the virus is clever enough to hide for the virusscanner.

I have no experience with linux-virusscanners, there are no linux-viruses out in the wild. Installing a virus scanner is something you don't have to do anymore in linux.

I use the McAfee Anti-Virus, Firewall and Privacy Protection for XP. Doesn't it check for viruses during the boot process? If I am not mistaken it does. I'll have to reboot then check the McAfee settings in XP. 

Before I download another scanner, which could cause some conflicts, I want to look at other options. Everything runs smooth when I am in my Windows partition. No indications of a possible infection. 

I'm not overly concerned about viruses in Linux. The scanner has already been removed. I guess that it was my curiosity more than anything else that led me to check it out. But, if it can help me to keep windows clean it could be useful.

---

### Post by tturrisi on 2006-11-23
As much as I frown upon any McAffee AVs or firewalls, in this case I would trust what it tells you about being clean.  It has the capabiliy of detecting & removing those named trojans:
[http://vil.nai.com/vil/content/v_99040.htm](http://vil.nai.com/vil/content/v_99040.htm)
[http://vil.nai.com/vil/content/v_101064.htm](http://vil.nai.com/vil/content/v_101064.htm)

The linux av possible registered a false positive.  I wouldn't worry about it.  Just for giggles, download and run HijackThis on windows & post the scan log here & I'll tell you if have anything to worry about.

---

### Post by ebozzz on 2006-11-23
> **tturrisi said:**
> As much as I frown upon any McAffee AVs or firewalls, in this case I would trust what it tells you about being clean.  It has the capabiliy of detecting & removing those named trojans:
[http://vil.nai.com/vil/content/v_99040.htm](http://vil.nai.com/vil/content/v_99040.htm)
[http://vil.nai.com/vil/content/v_101064.htm](http://vil.nai.com/vil/content/v_101064.htm)

The linux av possible registered a false positive.  I wouldn't worry about it.  Just for giggles, download and run HijackThis on windows & post the scan log here & I'll tell you if have anything to worry about.

I'll try to get download it later this evening. I wasn't really worried. I do most of what I have to do now in Ubuntu so I really don't even use that partition much. I mean I could even format it and re-install everything if necessary. Bot sure if that's need though. 

As for the McAfee products, I get it free from my ISP so that's the reason that I'm using it. As long as I am one of their customers I can download the suite on all of my PCs at no charge. I simply go to my account on the McAfee site, log in and download what I need. After the initial install I just let the automatic updates do their thing. Pretty nice benefit. I've now got 5 PCs in the house. I'm glad that I don't have to pay for licenses  on each of them. Have nice Thanksgiving if you celebrate the holiday. Thanks.

Charles

---

### Post by tturrisi on 2006-11-23
Understood re McAfee.
have a good holiday.

---

### Post by martexx on 2007-05-28
[CENTER]**STOP!!**[/CENTER]

what are they/you saying??!!!

**Never assume that these are false positives!!!**

I know this is an old thread but i am reading it and so are you.
If a person uses a virus-scanner on whatever OS and tells you it has found a virus 
it is wise not to say to him that it is a false positive.

The scanner seems to think it found something so go on and check it out!
if it is nothing then it is not,  ...but hey :) your scanning the files so why not take a look at them?
This Magistra virus/worm leaves a proof enough of its existense on a wndows desktop try a google search on it!

I run in to the same over here having 1 dual boot ubuntu / windows xp) and one xubunt install at my hand. I found that my windows suddenly stopped sometimes.
I tried Avast, Antivir and Mcaffee but none showed me a virus :(

I then whent one for a while but ran into these problems again,
I fired up ubuntu on the machine and ran aegis virus scanner


the results are schocking enough:
( i cant put the log file, it is to big, will come back on thiiiis later!


the only option left is to download a removal tool and hope that not to many files are corrupted.

(being infected is not the problem, this can be cured. But the corrupted files have to be manualy restored.... since this is undoable it will most likely mean a reinstall )


thank for your patience, and please!
no more talking about false positives ok?
It serves no goal and causes only more spreading of the worm

---

### Post by ebozzz on 2007-05-28
Good post! Thanks for contributing.

---

### Post by martexx on 2007-05-28
it keeps us all some safer :)

---

