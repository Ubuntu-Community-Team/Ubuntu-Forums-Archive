---
title: "Latest Kernel"
date: 2012-06-24
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kuvanito on 2012-06-24
after last kernel upgrade my logitech webcam stop working and the old ones that didn't work now work,what a mess!!!!

---

### Post by fjgaude on 2012-06-24
Such is the joy of Alpha testing, eh? My Dell mini-10 is in a kernel panic with 4.5. What to do now?

---

### Post by VinDSL on 2012-06-24
> **kuvanito said:**
> [...] what a mess!!!!

> **fjgaude said:**
> Such is the joy of Alpha testing [...]
Yes, sir!

We're past the point of no return now...  :D

---

### Post by kuvanito on 2012-06-24
yes testing is fun but it is still a mess ):P
any way,back to 12.04

---

### Post by Guilden_NL on 2012-06-24
Suggestion - test in a virtual environment unless you have a spare system laying around.

---

### Post by paul_in_london on 2012-06-24
Maybe try 3.5-rc4 from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-rc4-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-rc4-quantal/)

---

### Post by jerrylamos on 2012-06-24
> **Guilden_NL said:**
> Suggestion - test in a virtual environment unless you have a spare system laying around.

Multi-boot is another way, this one has four partitions - two Quantal i386, Quantal amd64, Precise,  I alternate on the i386's to test install and if one is broken I've a fallback.

Another PC I've got a 40 GB USB hard drive with two Quantal's and a Precise because I don't want to muck up the Windoze...7 on the main hard drive: my wife uses proprietary $$ software not offered on linux to support a couple web sites.

Another technique is to boot the .iso off the hard drive direct to see if the live Quantal has any quirks I don't want to install.

I write up a lot of launchpad bugs with new installs.  Good for testing.

Jerry

---

### Post by dino99 on 2012-06-26
will soon get a newer 3.5.0-2 into proposed archive based on rc4 ):P actually be built

---

### Post by philinux on 2012-06-26
[http://voices.canonical.com/kernelteam/2012/06/26/kernel-team-meeting-minutes-june-26-2012/](http://voices.canonical.com/kernelteam/2012/06/26/kernel-team-meeting-minutes-june-26-2012/)

---

### Post by zika on 2012-06-27
It seems that this new one (3.5.0-2) is working even for me... ;)
[http://ubuntuforums.org/showthread.php?t=1994605](http://ubuntuforums.org/showthread.php?t=1994605)

---

### Post by philinux on 2012-06-27
Looking good.

---

### Post by VinDSL on 2012-06-27
Glad it's working for you guys!  :)

I'm presuming that 3.5.2-2 is rebased from 3.5-rc4, and should cure a lot of problems, for all sorts of ppl. 

Gleaned from philinux's Kernel Team link, a few posts above:

> **[SIZE="+1"]ARM Status[/SIZE]**

Q/omap4: nothing new this week &#8211; for alpha2 we are going to use alpha1 kernel, but after we cut this milestone, work on a 3.5 &#8220;almost vanilla&#8221; kernel will immediately start.
Q/omap3: **[COLOR="DarkRed"]3.5rcX came with regressions in different subsets[/COLOR]** (video, mmc and usb) &#8211;**[COLOR="DarkRed"] a pending kernel (3.5.2-2) should have fixed all these issues.[/COLOR]**

> **[SIZE="+1"]Status: Quantal Development Kernel[/SIZE]**

[B][COLOR="DarkRed"]We have recently _rebased_ the Quantal kernel to the latest v3.5-rc4
upstream kernel and have also uploaded.[/COLOR][/B] We hope for this to land in the
Alpha 2 images. This also contains some critical bug fixes for omap3 and
i386 cloud images. It&#8217;s currently building in the quantal-proposed
pocket. This will also get uploaded to the q-lts-backport [1] PPA to
help facilitate testing of the 12.10 kernel in 12.04. We welcome any
early adopters to please install, test, and let us know your feedback.
[1] [https://launchpad.net/~ubuntu-x-swat/+archive/q-lts-backport](https://launchpad.net/~ubuntu-x-swat/+archive/q-lts-backport)
Important upcoming dates:

Thurs Jun 28 &#8211; Alpha 2 (2 days)
Thurs July 26 &#8211; Alpha 3 (~4 weeks)


Please, correct me, if I'm wrong...

---

### Post by philinux on 2012-06-27
> **VinDSL said:**
> Glad it's working for you guys!  :)

I'm presuming that 3.5.2-2 is rebased from 3.5-rc4, and should cure a lot of problems, for all sorts of ppl. 

Gleaned from philinux's Kernel Team link, a few posts above:

Please, correct me, if I'm wrong...

I'm on 3.5.0-2 which just came through the normal updates.

I think the 3.5.2 will come down the pipe later.

---

### Post by balloons on 2012-06-27
> **kuvanito said:**
> after last kernel upgrade my logitech webcam stop working and the old ones that didn't work now work,what a mess!!!!

Add yourself here. Looks like a kernel regression:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1018020](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1018020)

---

### Post by VinDSL on 2012-06-27
> **philinux said:**
> I'm on 3.5.0-2 which just came through the normal updates.

I think the 3.5.2 will come down the pipe later.
Good catch!  Thanks!

Heh!  I really shouldn't make technical posts at 3:00 AM  :D

---

### Post by ventrical on 2012-06-28
Even with system Monitor running this Dual Core is running as cool as a cucumber. with 3.5.0-2!

Sleek.

---

