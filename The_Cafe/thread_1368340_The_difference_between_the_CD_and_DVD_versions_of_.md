---
title: "The difference between the CD and DVD versions of Ubuntu"
date: 2009-12-30
forum: The Cafe
---

### Post by blueshiftoverwatch on 2009-12-30
I found out recently that you can download [ISO images]("http://cdimage.ubuntu.com/releases/9.10/release/") of Ubuntu on DVD instead of the standard CD. Apparently it's not well advertised.

What exactly is the difference between the two? Does the DVD install more software (like build essential packages and stuff like that) or libraries by default? Or is the install exactly the same as the CD version of Ubuntu with the exception that when your getting software from apt-get/Synaptic you can choose to install from the DVD instead of the Internet in case you have a slower connection?

---

### Post by Gizenshya on 2009-12-30
I don't know about this specific release, but they are usually just releases with tons of extra software you might want.

best to order one or download from a fast connetion, though...

```
$ wget -c http://cdimage.ubuntu.com/releases/9.10/release/ubuntu-9
.10-dvd-amd64.iso
--2009-12-30 14:20:58--  http://cdimage.ubuntu.com/releases/9.10/release/ubuntu-
9.10-dvd-amd64.iso
Resolving cdimage.ubuntu.com... 91.189.88.34
Connecting to cdimage.ubuntu.com|91.189.88.34|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 4174614528 (3.9G), 4173993278 (3.9G) remaining [application/x-iso9660-im
age]
Saving to: `ubuntu-9.10-dvd-amd64.iso'

 0% [                                       ] 790,223     2.14K/s  eta 6d 44h
```

Only 6 days and... 44 hours to go (wtf? lol).  If I can keep my average at 2.14 K/s, that is :p

and for those who didn't get it, I was just curious.  I'm not actually going to download that with a 56k hahaha

---

### Post by Xbehave on 2009-12-30
> **blueshiftoverwatch said:**
> Or is the install exactly the same as the CD version of Ubuntu with the exception that when your getting software from apt-get/Synaptic you can choose to install from the DVD instead of the Internet in case you have a slower connection?
This, i think you can also install said software from the dvd while using it as a liveDVD without using as much ram as if you did the same on a liveCD

---

### Post by Frak on 2009-12-30
Same install, just more software available on the disc.

---

### Post by blueshiftoverwatch on 2009-12-30
> **Frak said:**
> Same install, just more software available on the disc.
If I wasn't allotted 250GB of bandwidth per month from Comcast I'd feel like I just wasted time downloading and burning the DVD ISO image.

---

### Post by Frak on 2009-12-30
> **blueshiftoverwatch said:**
> If I wasn't allotted 250GB of bandwidth per month from Comcast I'd feel like I just wasted time downloading and burning the DVD ISO image.
I'm allotted unlimited bandwidth from AT&T, and I do feel I wasted my time burning a DVD. I no longer burn Ubuntu DVD's, since I have access to the internet, i.e. newer software.

---

### Post by Roasted on 2009-12-30
> **Frak said:**
> Same install, just more software available on the disc.

Does the DVD have options where you can check off stuff like other distros?

Check - Yes I'd like Samba installed.
Check - Yes I'd like restricted extras installed.
Check - Yes I'd like mp3 support enabled.
Uncheck - Nah I don't need LAMP server services enabled by default.
Apply
Okay
Install


Also - Does the DVD come with more than one desktop environment? Be nice if *buntu came with XFCE, KDE, and Gnome all bundled into one install DVD.

---

### Post by Frak on 2009-12-30
> **Roasted said:**
> Does the DVD have options where you can check off stuff like other distros?

Check - Yes I'd like Samba installed.
Check - Yes I'd like restricted extras installed.
Check - Yes I'd like mp3 support enabled.
Uncheck - Nah I don't need LAMP server services enabled by default.
Apply
Okay
Install


Also - Does the DVD come with more than one desktop environment? Be nice if *buntu came with XFCE, KDE, and Gnome all bundled into one install DVD.
I don't think so. Everytime I've used it, it just acted as a normal Ubuntu install. There's probably other DE's on the disc, but it's not made readily apparent.

---

### Post by Techsnap on 2009-12-30
Unlike Most distros the Ubuntu DVD offers absolutely no customisation to packages during the installation. It just contains all the software from the main repos so you don't need an internet connection each time you want to download them. The default installation is EXACTLY the same as if you was to install straight off the CD.

Unless you have a slow connection or you're installing it on a whole lot of computers you're wasting time downloading the DVD.

---

### Post by blueshiftoverwatch on 2009-12-30
> **Techsnap said:**
> Unlike Most distros the Ubuntu DVD offers absolutely no customisation to packages during the installation. It just contains all the software from the main repos so you don't need an internet connection each time you want to download them. The default installation is EXACTLY the same as if you was to install straight off the CD.
That sounds pretty jank. I like the idea of allowing the user to install optional packages. Like the software necessary for compiling source code. I downloaded the Ubuntu 9.10 CD from Bittorrent and seeded over 1:1. So at least in my case they wouldn't be paying any extra in bandwidth costs because if given the option I'd rather download the DVD and get more essential packages installed by default.

---

### Post by Dhrishtadyumna on 2009-12-30
According to [http://www.ubuntu.com/getubuntu/downloadmirrors#dvd](http://www.ubuntu.com/getubuntu/downloadmirrors#dvd) , the only advantage of DVD is to get access to all of the available language packs

---

### Post by koleoptero on 2009-12-30
> **Dhrishtadyumna said:**
> According to [http://www.ubuntu.com/getubuntu/downloadmirrors#dvd](http://www.ubuntu.com/getubuntu/downloadmirrors#dvd) , the only advantage of DVD is to get access to all of the available language packs

^ This.

There are no additional software, only more language packs. If you install from a cd it tells you to download the gull language support separately (if you use a language other than English that is). If you use the DVD you get that without an internet connection.

And a biiig LOL @ Techsnap: It would take several bluray disks to have all the software in the repos with you. Think people think. And do your research :P

EDIT: [Take a look at what I mean.]("http://packages.ubuntu.com/karmic/allpackages")

EDIT 2: [And another look, more informative.]("http://ubuntuforums.org/showthread.php?t=352460")

Google is an amazing tool :P

---

### Post by Frak on 2009-12-30
> **koleoptero said:**
> ^ This.

There are no additional software, only more language packs. If you install from a cd it tells you to download the gull language support separately (if you use a language other than English that is). If you use the DVD you get that without an internet connection.

And a biiig LOL @ Techsnap: It would take several bluray disks to have all the software in the repos with you. Think people think. And do your research :P

EDIT: [Take a look at what I mean.]("http://packages.ubuntu.com/karmic/allpackages")

EDIT 2: [And another look, more informative.]("http://ubuntuforums.org/showthread.php?t=352460")

Google is an amazing tool :P
He said **Main Repos**. The **Main Repos** are actually quite small. Fail.

---

### Post by Xbehave on 2009-12-30
> **blueshiftoverwatch said:**
> That sounds pretty jank. I like the idea of allowing the user to install optional packages. 
You can, just use apt-get/tasksel but with the dvd in.

---

