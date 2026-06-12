---
title: "Windows emulator/virtual computer?"
date: 2008-08-12
forum: Virtualisation
---

### Post by zx6r1033 on 2008-08-12
I'm not sure where this should have been posted, so it landed here. 

Anyway...

I have netflix, and I would still like to watch their "instant" movies. The problem is, they require Windows and IE. I know ies4linux can take care of the IE end of this, but I need something that will fool netflix into thinking I have windows (and a way to run their plugin). I am not sure if Wine will handle this or if I would have to look elsewhere to solve the problem. I haven't tried using Wine much, so I don't know exactly how it works or what it is capable of.

---

### Post by tuxxy on 2008-08-12
You could install virtualbox and run a virtual windows from in Ubuntu, this is available in the repos, search for virtualbox in synaptic or open terminal and type

```
sudo apt-get install virtualbox*
```

Heres a good doc for you, for setting up a virtual drive and installation :)

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by zx6r1033 on 2008-08-12
Thanks. I was looking at that just a moment ago, but their site listed only the source code. To be honest, I have had ubuntu for the past week, and I think my head is about to explode from all of the commands I've had to run in the terminal to make various things work. 

They have various parts of Virtualbox listed in the Synaptic Package Manager, as well. I am finding this to be the case with most of the programs I have spent long periods of time in terminal trying to install, only to later discover them in spm. In this case, though, I cannot figure out which part of it I would need, and I have already had to reinstall on my laptop 4 times due to mistakes I've made in terminal. 

I'm off topic and rambling now... I'll stop. lol. 

Thanks again.


Edit: followed the instructions, got an error message.

> the following packages have unmet dependencies:
   Virtualbox-ose-modules-generic: Depends: Virtualbox-ose-modules-2.6.24-20-generic but is not going to be installed
E: Broken packages

---

### Post by Ryadt on 2008-08-12
```
sudo apt-get install virtualbox-ose
```will install it.

---

### Post by Ezlo4 on 2008-08-12
Okay I decided to use this. Everytime I try to start up my system, it says that the VirtualBox kernel driver is not installed.

---

### Post by zx6r1033 on 2008-08-12
> **Ryadt said:**
> ```
sudo apt-get install virtualbox-ose
```will install it.


Got it... Thank you!

Man, you guys are life savers. If it wasn't for this place, I think I would have scrapped Ubuntu and gone running back to XP with my tail between my legs long ago. That would have been a shame... Ubuntu is so much better.

---

### Post by zx6r1033 on 2008-08-12
Ugh. #-o  I got the same message as the above poster - 


> **Ezlo4 said:**
> Okay I decided to use this. Everytime I try to start up my system, it says that the VirtualBox kernel driver is not installed.

---

### Post by Ryadt on 2008-08-12
Ok. Uninstall this one and follow this guid to install the latest one from there website.[http://ubuntuforums.org/showthread.php?t=770745&highlight=virtualbox](http://ubuntuforums.org/showthread.php?t=770745&highlight=virtualbox)

---

### Post by kernelhaxor on 2008-08-12
If you dont mind closed source software, I recommend you install virtualbox by downloading it from its website and installing it urself .. because that closed source version has a lot more features than the open sourced version that you get from the repos ..For example: USB support isnt available in the open source version but is available in the closed source version .. 
Just letting u know because I had to reinstall mine as I needed USB support for my Ipod

---

### Post by bodhi.zazen on 2008-08-12
The OSE (Open Source Edition) has issues.

I advise the edition from the Sun site (PUEL)

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

---

### Post by zx6r1033 on 2008-08-12
> **bodhi.zazen said:**
> The OSE (Open Source Edition) has issues.

I advise the edition from the Sun site (PUEL)

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)



That just crashed my desktop and loaded my boot menu with about 100 options for different kernals. 

I am now in the process of reloading. :(

---

### Post by bodhi.zazen on 2008-08-12
> **zx6r1033 said:**
> That just crashed my desktop and loaded my boot menu with about 100 options for different kernals. 

I am now in the process of reloading. :(

That sounds very very unusual, never head of anything remotely like that due to Sun Virtualbox-*.deb.

Screenshot ?

---

### Post by zx6r1033 on 2008-08-12
> **bodhi.zazen said:**
> That sounds very very unusual, never head of anything remotely like that due to Sun Virtualbox-*.deb.

Screenshot ?

If I had thought of it, I would have. I have already wiped and reinstalled, though. Sorry.

---

### Post by zx6r1033 on 2008-08-12
I just reinstalled the program and granted myself user access. The program won't start, though. It says the boot medium could not be found. 


:-k

---

### Post by tuxxy on 2008-08-12
If all you want windows for is IE and movies im sure the virtualbox in the repos will allow you to do this.  I have it running here and for them purposes it does the job

---

### Post by pparks1 on 2008-08-12
While you are at it, i suggest sending a message off to Netflix and let them know that you are disappointed that they only support Windows and IE.   I'm going to do the same thing myself, as I've been a Netflix customer since June of 2001.   I know it's likely not something that they are likely to correct anytime soon...but people shouldn't be forced into particular OS's and software for functionality like this.

---

### Post by zx6r1033 on 2008-08-12
> **pparks1 said:**
> While you are at it, i suggest sending a message off to Netflix and let them know that you are disappointed that they only support Windows and IE.   I'm going to do the same thing myself, as I've been a Netflix customer since June of 2001.   I know it's likely not something that they are likely to correct anytime soon...but people shouldn't be forced into particular OS's and software for functionality like this.

I've done that, too. I remember seeing a thread floating around here about netflix not that long ago. It is really quite disappointing to me that they would have it set up the way they do, but they obviously have no intention of ever fixing it.

---

### Post by zx6r1033 on 2008-08-12
Oh... I completely spaced. If you check their [FAQ]("http://www.netflix.com/FAQ?p_faqid=2883"), this is what they have to say:

> 
Q:
Can I watch instantly using Firefox or another web browser?

A:
Our goal is for Netflix members to enjoy movies and TV shows on whatever screen or browser they want. We will be expanding the platforms supported by the Netflix Movie Viewer over the coming year.

---

