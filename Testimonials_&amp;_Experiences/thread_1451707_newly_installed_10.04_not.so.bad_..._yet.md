---
title: "newly installed 10.04 not.so.bad ... yet"
date: 2010-04-10
forum: Testimonials &amp; Experiences
---

### Post by nss0000 on 2010-04-10
Gents:

Running AMD_965/MSI-gd70/BFG_9800gtx+ ... 

Yesterday evening I burned the x64-Luxy_Lynx.iso; this evening I installed it  < destroying a U_9.1 setup > plus various fellow_travelers. Lots worked automagically:

4xCPU : 500-GSata : 6-G Crucial ram : 9800gtx support : found shared HP1300 laserjet: WWW auto-established(? whatever) :     

The obvious flaws were as expected:

 no default NV 190.xxx driver boohoo : 2nd Sata-HDD NOT auto configured(?)... it just sorta hangs_out like I didn't want to use it !

---

### Post by uRock on 2010-04-10
I am using the new open source driver for nvidia(Nouveau) and it is doing great.

Cheers,
Ronnie

---

### Post by 3rdalbum on 2010-04-11
> **nss0000 said:**
> 
The obvious flaws were as expected:

 no default NV 190.xxx driver boohoo

That's not really a flaw. If Ubuntu wanted to, it could automatically install the Nvidia driver by default. However, Ubuntu has a commitment to Free Software, and the Nvidia driver is not Free (it's free of charge, but not Free as in Freedom).

Ubuntu 10.04 ships with the Free "Nouveau" 2D driver for your hardware. If you want Nvidia's own 3D driver (version 195) it's pretty easy to enable - just go to System > Administration > Hardware Drivers and click the "Activate" button to download and install it.

I do find it odd that Ubuntu 10.04 doesn't have an easy way of installing the experimental Nouveau 3D support. I'd love to test it, but I don't want to go messing with PPAs or compiling it for myself - the last time I tried that with a computer, I completely broke X.

---

### Post by uRock on 2010-04-11
> **3rdalbum said:**
> I do find it odd that Ubuntu 10.04 doesn't have an easy way of installing the experimental Nouveau 3D support. I'd love to test it, but I don't want to go messing with PPAs or compiling it for myself - the last time I tried that with a computer, I completely broke X.

I'd like to test it too, but I am too lazy to do the compiling. So far I am pleased with the 2D. Sooner or later I would like to have compiz going again.

---

### Post by nss0000 on 2010-04-11
> **3rdalbum said:**
> That's not really a flaw. If Ubuntu wanted to, it could automatically install the Nvidia driver by default. However, Ubuntu has a commitment to Free Software, and the Nvidia driver is not Free (it's free of charge, but not Free as in Freedom).

Ubuntu 10.04 ships with the Free "Nouveau" 2D driver for your hardware. If you want Nvidia's own 3D driver (version 195) it's pretty easy to enable - just go to System > Administration > Hardware Drivers and click the "Activate" button to download and install it.

I do find it odd that Ubuntu 10.04 doesn't have an easy way of installing the experimental Nouveau 3D support. I'd love to test it, but I don't want to go messing with PPAs or compiling it for myself - the last time I tried that with a computer, I completely broke X.

That SYS --> ADMIN --> HWDrivers method **failed** on my system. I allowed writing_out the report as I try to help given my meager skills.  

Ubuntu **may be** , but I am not committed to free software ... or free anything. Historically I have sought-out **freeware** authors to fairly pay them for their effort. I **approve** of a common_payment < say $100 > for Ubuntu software ... such a cost will eliminate the riff-raff. 

As for flaw --- anything less-than-the-best is by-definition a **flaw**. The NV_pro driver has.been.reported 5x-faster than the open-source driver.

---

### Post by nss0000 on 2010-04-11
Gents:

Continuing the move from U_9,1 to x64LL_10.04:

The NV_drivers appeared automagically **after** an error mesage claiming the install had failed. 

UTube vids just work.

GoogleEarth installed without issue.

--HOWEVER--
HDD_tool has attractive GUI, but **not** self explainatory for enabling a 2nd HDD. It it data-orientated, but not **task** oriented ... you know, like concrete-nouns and active-verbs.

---

### Post by nss0000 on 2010-04-11
Various aud/vid proggies installed ... DVDs still unplayable.

---

### Post by uRock on 2010-04-11
Run the following two commands to install the Medibuntu repository and install the app needed to decrypt the dvd.

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

```
sudo apt-get install libdvdcss2
```

---

### Post by nss0000 on 2010-04-11
> **uRock said:**
> Run the following two commands to install the Medibuntu repository and install the app needed to decrypt the dvd.

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

```
sudo apt-get install libdvdcss2
```

Yep! Major thanks for the clue! Not only my Vid_DVDs, but also music_CDs now play. 

All things considered the new x64luxxy_Lynx looks like a gem.

---

### Post by craig10x on 2010-04-11
> **uRock said:**
> Run the following two commands to install the Medibuntu repository and install the app needed to decrypt the dvd.

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
``````
sudo apt-get install libdvdcss2
```

Just curious...but would you use the exact same commands in the terminal if you are using 64 bit as opposed to 32 bit version of Ubuntu?

Also...could one install Ubuntu Restricted Extras and then just add on the encrypted dvd plug in?  If so, would you just enter the second command you gave?

Thanks :)

---

### Post by uRock on 2010-04-11
> **craig10x said:**
> Just curious...but would you use the exact same commands in the terminal if you are using 64 bit as opposed to 32 bit version of Ubuntu?

Also...could one install Ubuntu Restricted Extras and then just add on the encrypted dvd plug in?  If so, would you just enter the second command you gave?

Thanks :)

Medibuntu works with 32 and 64 bit systems. Ubuntu-restricted-extras doesn't have the libdvdcss2 needed for running encrypted DVDs.

For more on Medibuntu, please see [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Cheers,
Ronnie

---

### Post by 3rdalbum on 2010-04-12
> **nss0000 said:**
> That SYS --> ADMIN --> HWDrivers method **failed** on my system. I allowed writing_out the report as I try to help given my meager skills.

Good stuff, thanks for writing a bug report.

> Ubuntu **may be** , but I am not committed to free software ... or free anything.

That's fine. I don't have a problem with your position. Neither does Ubuntu - that's why Ubuntu provides a way for you to activate said drivers by your own choice. When it works.

> Historically I have sought-out **freeware** authors to fairly pay them for their effort. I **approve** of a common_payment < say $100 > for Ubuntu software ... such a cost will eliminate the riff-raff.

Ubuntu is not an elitist club. That's the image that Linux is trying to shake off! Also, although it's permissable to charge for Linux, you must provide the source code on request to comply with the GPL (software license that Linux uses). This means that anybody could get the source code and recompile it without Ubuntu trademarks, just like what CentOS does with Red Hat.

> As for flaw --- anything less-than-the-best is by-definition a **flaw**. The NV_pro driver has.been.reported 5x-faster than the open-source driver.

If you believe in proprietary software being a restriction of one's freedom, then shipping with proprietary software is a flaw. Ubuntu takes a pragmatic approach to software freedom: If the computer can't be used without non-Free software, then include it. If there is a choice between Free software and non-Free, then choose the Free and give the user the ability to choose.

Also note that Canonical has to provide support for Ubuntu, in the way of bugfixes and security fixes and such. They can't do that with proprietary drivers.

Anyway I'm glad you still like Ubuntu.

---

### Post by nss0000 on 2010-04-28
> **3rdalbum said:**
> Good stuff, thanks for writing a bug report.



That's fine. I don't have a problem with your position. Neither does Ubuntu - that's why Ubuntu provides a way for you to activate said drivers by your own choice. When it works.



Ubuntu is not an elitist club. That's the image that Linux is trying to shake off! Also, although it's permissable to charge for Linux, you must provide the source code on request to comply with the GPL (software license that Linux uses). This means that anybody could get the source code and recompile it without Ubuntu trademarks, just like what CentOS does with Red Hat.

If you believe in proprietary software being a restriction of one's freedom, then shipping with proprietary software is a flaw. Ubuntu takes a pragmatic approach to software freedom: If the computer can't be used without non-Free software, then include it. If there is a choice between Free software and non-Free, then choose the Free and give the user the ability to choose.

Also note that Canonical has to provide support for Ubuntu, in the way of bugfixes and security fixes and such. They can't do that with proprietary drivers.

Anyway I'm glad you still like Ubuntu.

Neither unalloyed freedom/slavery provides the most robust & productive human environs -- shrill and sanctimonious Libertoonian and Stalinist rappers to the contrary. 

Successful self-structuring behavior ( in non-linear systems ) requires "middling" values for all relevant parameters. Thus encouraging rich/poor lusrlanders to fork-over $100 for UBUNTU would be **ideal**. True equality means equal pain and nothing hurts like paying for something. 

That self.imposed pain also provides an ironic, needed and amuzing smackdown to the Debiolian and Slackmonian byteboyz elitists. They will **truly** fear for the viability of BASH.shell horrors as for.profit coders usrize all Linux interfaces.

---

### Post by marshmallow1304 on 2010-04-29
I would consider it insulting for someone to put a price tag on something that I created and gave freely for the collective good.  Not everyone views the world in terms of $ and £.

---

### Post by Tamlynmac on 2010-04-29
I'm not certain why this thread didn't get posted in the help sections?

When considering upgrading it's been expressed many time in this forum that one should always confirm upgrade compatibility prior to upgrading. A quick search of this section alone will reveal many such helpful explanations as to how. Upgrading without taking precautions is hazardous and not doing a system backup prior is a flawed plan. 

The simple fact remains that each and every one us assumes the responsibility for upgrading our systems. Logic suggests we take measures to assure said upgrade is compatible and will not only prove functional, but enhance our experience. It's been my experience that all OS's have hardware restrictions and often systems react poorly to OS's that aren't compatible.

Might I recommend that one do some research prior to upgrading and identify if said upgrade is not only compatible, but that it will actually improve your system's functionality. Not to mention if it's even necessary. Choice...

Good Luck

Since this isn't a debating section of the forum, I will not argue with the responses of others.

---

