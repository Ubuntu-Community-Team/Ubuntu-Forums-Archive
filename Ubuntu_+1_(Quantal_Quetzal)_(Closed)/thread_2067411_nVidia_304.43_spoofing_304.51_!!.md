---
title: "nVidia 304.43 spoofing 304.51 ?!?!?"
date: 2012-10-06
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by VinDSL on 2012-10-06
Gotta say, in all my years of testing, I've never seen this one before...

```
vindsl@Zuul:~$ dpkg --status nvidia-current | grep Version | cut -f 1 -d '-'
**[COLOR="Red"]Version: 304.51.really.304.43[/COLOR]**

```

Er... 

Can anyone explain how/why 'they' did this?  :D

---

### Post by funicorn on 2012-10-06
Because they claimed 304.51 is buggy in Unity, I found it works very well though.
304.43 is a Beta. 304.51 is NOT.

---

### Post by VinDSL on 2012-10-06
Understood, but...

nVidia is being reported as "304.51.really.304.43"

How are we supposed to cut code around that?

---

### Post by VinDSL on 2012-10-06
Let's play "Magic 8-Ball".

Hrm... 

I wonder what version of nvidia-current I'm running.  Let's parse it out...

```
vindsl@Zuul:~$ dpkg --status nvidia-current | grep Version
**[COLOR="Red"]Version: 304.51.really.304.43-0ubuntu1[/COLOR]**
```
Who?
```
vindsl@Zuul:~$ dpkg --status nvidia-current | grep Version | cut -f 1 -d '-'
**[COLOR="Red"]Version: 304.51.really.304.43[/COLOR]**
```
What?
```
vindsl@Zuul:~$ dpkg --status nvidia-current | grep Version | cut -f 1 -d '-' | sed 's/[^.,0-9]//g'
**[COLOR="Red"]304.51..304.43[/COLOR]**

```
Huh?

What are we supposed to do with output like that?  LoL!  :D

---

### Post by funicorn on 2012-10-06
yes, this naming rule is ridiculous. and u can find another example: 
nautilus    1:3.5.90.really.3.4.2-0ubuntu4

and I found xxx.really.yyy is taken as a higher version than xxx itself. That's even more ridiculous, when xxx is larger than yyy.

 
> **VinDSL said:**
> Understood, but...

nVidia is being reported as "304.51.really.304.43"

How are we supposed to cut code around that?

---

### Post by cariboo on 2012-10-06
I'm still using 304.51 here:

```
dpkg --status nvidia-current-updates | grep Version
Version: 304.51-0ubuntu1
```

---

### Post by VinDSL on 2012-10-06
Just found this...

SOURCE:  [https://launchpad.net/ubuntu/quantal/+source/nvidia-graphics-drivers/304.51.really.304.43-0ubuntu1](https://launchpad.net/ubuntu/quantal/+source/nvidia-graphics-drivers/304.51.really.304.43-0ubuntu1)
> Format: 1.8
Date: Fri, 05 Oct 2012 18:52:59 +0200
Source: nvidia-graphics-drivers
Binary: nvidia-current nvidia-current-dev
Architecture: source
Version: 304.51.really.304.43-0ubuntu1
Distribution: quantal
Urgency: low
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Changed-By: Alberto Milone <alberto.milone@canonical.com>
Description: 
 nvidia-current - NVIDIA binary Xorg driver, kernel module and VDPAU library
 nvidia-current-dev - NVIDIA binary Xorg driver development files
Launchpad-Bugs-Fixed: 950963 1057000
Changes: 
 nvidia-graphics-drivers (304.51.really.304.43-0ubuntu1) quantal; urgency=low
 .
   * Revert to 304.43 (LP: #1057000).
   * debian/nvidia-current.dirs.in:
     - Add /usr/share/applications. This should fix
       nvidia-cuda-toolkit FTBFS (LP: #950963).
   * debian/nvidia-current.{postinst|prerm}.in,
     debian/rules:
     - Make sure that the packaging knows how to deal with
       reverted versions such as this one.
Checksums-Sha1: 
 feb1c6fd7df18ea34d8bb01401617bb713303e42 1623 nvidia-graphics-drivers_304.51.really.304.43-0ubuntu1.dsc
 53cedb5ebf0100918cab9cac667c9718064cabfc 77197913 nvidia-graphics-drivers_304.51.really.304.43.orig.tar.gz
 6974a5dfc1446338c0c8dac62c216fef083e7d7d 159205 nvidia-graphics-drivers_304.51.really.304.43-0ubuntu1.diff.gz
Checksums-Sha256: 
 7cacfe74655ef1b6806ba1c8c25b0ef896528ad4e16f2fdce3d52959dacc8a91 1623 nvidia-graphics-drivers_304.51.really.304.43-0ubuntu1.dsc
 5342507f6c9e3221dc4f5b085c290a53791b69d026749e825b1502c91bd4b6a8 77197913 nvidia-graphics-drivers_304.51.really.304.43.orig.tar.gz
 8c37769ec06a9c52a064e2c364439d2ecb7414bca3e8f0de8a17c67b6eba2f47 159205 nvidia-graphics-drivers_304.51.really.304.43-0ubuntu1.diff.gz
Files: 
 b5c0a450e93ed93fa6283ad7a049e4d8 1623 restricted/misc optional nvidia-graphics-drivers_304.51.really.304.43-0ubuntu1.dsc
 7ecd1ad6b41dd29c1d9d82f42865cf44 77197913 restricted/misc optional nvidia-graphics-drivers_304.51.really.304.43.orig.tar.gz
 406379567b2a1f0b605bd99f43c1e961 159205 restricted/misc optional nvidia-graphics-drivers_304.51.really.304.43-0ubuntu1.diff.gz

If they were going to revert back to 304.43, fine, but why did they spoof the name?  

Either it's "really" 304.43 or 304.51. yes?

Heh!  This one has me scratching my head!

---

### Post by VinDSL on 2012-10-06
> **cariboo907 said:**
> I'm still using 304.51 here:

```
dpkg --status nvidia-current-updates | grep Version
Version: 304.51-0ubuntu1
```
That's what I'm going to do, too... revert back to the "really real 304.51" version.  :)

This is silly...

---

### Post by VinDSL on 2012-10-06
OK, that works (still sitting in my cache).  ;)

```
vindsl@Zuul:~$ dpkg --status nvidia-current | grep Version
Version: 304.51-0ubuntu1~xedgers~quantal1
```

Forced/pinned...

---

### Post by funicorn on 2012-10-06
I use apt-fast. Before genuine upgrade I found nvidia-current is in the list, hence held it. Just waste 64MB flow and 500J electricity, I'm glad not be an environmentalist.

---

### Post by VinDSL on 2012-10-06
> **funicorn said:**
> yes, this naming rule is ridiculous. and u can find another example: 
nautilus    1:3.5.90.really.3.4.2-0ubuntu4

and I found xxx.really.yyy is taken as a higher version than xxx itself. That's even more ridiculous, when xxx is larger than yyy.
Interesting!

This is the first time I've seen it, and had a shock reaction.

Too much coffee, today, I guess... LoL!  :D

---

### Post by VinDSL on 2012-10-06
> **funicorn said:**
> I use apt-fast. Before genuine upgrade I found nvidia-current is in the list, hence held it. Just waste 64MB flow and 500J electricity, I'm glad not be an environmentalist.
Bwahahaha! Reminds me of the US jobless rate...

It was >= 8% for 3 1/2 years. Now, suddenly, it's "7.8.really.14.6"  :D

---

