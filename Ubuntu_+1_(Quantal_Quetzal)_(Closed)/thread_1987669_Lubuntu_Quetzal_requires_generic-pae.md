---
title: "Lubuntu Quetzal requires generic-pae"
date: 2012-05-26
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jerrylamos on 2012-05-26
Finally lubuntu quantal quetzal .iso i386 image showed up in [http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)
but didn't do me any good.

Tried booting .iso from hard drive.  
Works on precise, oneiric, maverick, lucid, ....  Not this time.  Squashfs unable to read block xxx

Tried mounting loop mode onto a 1G hard drive partition and booting.  
Works on precise, oneiric, maverick, lucid, ....  Not this time.  Squashfs unable to read block xxx
   
Used dd to copy the .iso to a USB stick to see if it would do a hybrid boot.
Ooof.  dd must copy bit - by - bit - s -- l -- o -- w -- l -- y -- ....

Needn't have bothered.  

"Kernel requires pae".

No QQ on this notebook.  Ever...

Actually Lucid Lynx running fine (!!) nicely responsive, fast, capable, functional, great wireless, and when support is dropped, I'll go to Precise Pangolin lubuntu.  

For Precise I'll have to buy a wireless card since PP doesn't support AIRONET Wireless Communications Cisco Aironet Wireless 802.11b.  Launchpad Bug written.  Connects fine, then the kernel disconnects it.  Connects again, kernel disconnects, repeat.  Ad nauseum. Until I manually select the wireless applet and disconnect.

Jerry

---

### Post by pressureman on 2012-05-26
You can't expect to run the latest OS on old hardware forever...

I used to have a 286, that could never run Windows 95.... gutted.

;-)

---

### Post by MG&amp;TL on 2012-05-26
We did have this discussion on the mailing list (although I must say, I don't recall the outcome)...maybe it would be helpful for you to join it? Not criticising, just giving you the opportunity to say 'I will be affected' next time. :)

---

### Post by pressureman on 2012-05-26
You could also just compile your own non-pae kernel. It's not like the support for non-pae hardware is being dropped from Linux itself (yet)... just that Ubuntu no longer packages such kernels.

Or you could simply stick to 12.04 LTS on that hardware. Let's be honest - by the time 12.04 reaches EOL, is that hardware *really* still going to be relevant?

The fact that you mention an 802.11b card is also indicative of how outdated that setup is... I haven't seen an 802.11b card for close to ten years! They wouldn't keep up with most ADSL connections these days, getting only around 4-5 Mbps under ideal conditions.

---

### Post by MG&amp;TL on 2012-05-26
> **pressureman said:**
> 
Or you could simply stick to 12.04 LTS on that hardware. Let's be honest - by the time 12.04 reaches EOL, is that hardware *really* still going to be relevant?

Lubuntu 12.04 is not LTS. Although you might have a point with the hardware. ;)

---

### Post by Yellow Pasque on 2012-05-26
There will be no more non-pae kernel in QQ: [https://lists.ubuntu.com/archives/ubuntu-devel/2012-May/035176.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-May/035176.html)

> IIRC a non-PAE
kernel was installed because 1) there was less then 4GB RAM, or 2) their
CPU did not have PAE support.

The folks in case 2 are simply out of luck (and no longer supported).

So, you're SOL (simply out of luck). ;P

---

### Post by kansasnoob on 2012-05-26
> **jerrylamos said:**
> Finally lubuntu quantal quetzal .iso i386 image showed up in [http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)
but didn't do me any good.

Tried booting .iso from hard drive.  
Works on precise, oneiric, maverick, lucid, ....  Not this time.  Squashfs unable to read block xxx

Tried mounting loop mode onto a 1G hard drive partition and booting.  
Works on precise, oneiric, maverick, lucid, ....  Not this time.  Squashfs unable to read block xxx
   
Used dd to copy the .iso to a USB stick to see if it would do a hybrid boot.
Ooof.  dd must copy bit - by - bit - s -- l -- o -- w -- l -- y -- ....

Needn't have bothered.  

"Kernel requires pae".

No QQ on this notebook.  Ever...

Actually Lucid Lynx running fine (!!) nicely responsive, fast, capable, functional, great wireless, and when support is dropped, I'll go to Precise Pangolin lubuntu.  

For Precise I'll have to buy a wireless card since PP doesn't support AIRONET Wireless Communications Cisco Aironet Wireless 802.11b.  Launchpad Bug written.  Connects fine, then the kernel disconnects it.  Connects again, kernel disconnects, repeat.  Ad nauseum. Until I manually select the wireless applet and disconnect.

Jerry

You shouldn't be surprised having taken part in PP testing ;)

Were it not for the diligence of Colin Watson even Precise would have had no non-pae kernel option.

I've tested [Precise classic (no effects)]("http://ubuntuforums.org/showthread.php?t=1966370") on as little as an 1100mHz CPU w/1GB of RAM and it roars like a lion ......... and it's supported for 5 years :D

---

### Post by xebian on 2012-05-26
But you can still run QQ with a non-pae kernel.  Just get the PP kernel, and you should be ok.

---

### Post by kansasnoob on 2012-05-26
> **xebian said:**
> But you can still run QQ with a non-pae kernel.  Just get the PP kernel, and you should be ok.

But if you're going to run a Precise kernel why not just run Precise as a whole :confused:

It will have five years of security support. If someone has a problem with a certain app they can ask for it to be added to [backports]("https://wiki.ubuntu.com/UbuntuBackports").

---

### Post by xebian on 2012-05-26
> **kansasnoob said:**
> But if you're going to run a Precise kernel why not just run Precise as a whole :confused:

It will have five years of security support. If someone has a problem with a certain app they can ask for it to be added to [backports]("https://wiki.ubuntu.com/UbuntuBackports").

True, but backports may not happen at all.  

Running PP's kernel is like driving last year engine with this year's body style.  You get the latest applications which I think will run nicely with previous as much as with latest kernel.

---

### Post by kansasnoob on 2012-05-26
> **xebian said:**
> True, but backports may not happen at all.  

Running PP's kernel is like driving last year engine with this year's body style.  You get the latest applications which I think will run nicely with previous as much as with latest kernel.

But you'd first have to use a PC that can run the pae kernel, switch that install to the older kernel, and then remaster a new iso to be able to install it to a non-pae box :p

Hardly a piece of cake.

---

### Post by xebian on 2012-05-26
> **kansasnoob said:**
> But you'd first have to use a PC that can run the pae kernel, switch that install to the older kernel, and then remaster a new iso to be able to install it to a non-pae box :p

Hardly a piece of cake.

There is an easier way.  Boot a PP netboot and just install the base no desktop just command line.  Upgrade to QQ first and then install your fav desktop.

---

### Post by jerrylamos on 2012-05-26
> **xebian said:**
> There is an easier way.  Boot a PP netboot and just install the base no desktop just command line.  Upgrade to QQ first and then install your fav desktop.
Actually I do have a partition with PP lubuntu generic upgraded to QQ lubuntu generic.  I was trying for a new install in another partition just because install has been so buggy it is usually good for some Launchpad bug postings.

Usual Microsoft Mantra, "This new Windows XX is so good you have to buy a newer faster pc to do what you used to do on the older Windows...."

Jerry

---

### Post by pressureman on 2012-05-26
> **jerrylamos said:**
> Usual Microsoft Mantra, "This new Windows XX is so good you have to buy a newer faster pc to do what you used to do on the older Windows...."

I think that's a little unfair... as a developer myself, I am constantly trying to take advantage of new hardware or OS capabilities. Sometimes, you have to draw a line in the sand and deprecate support for older hardware, in order to move forward.

If newer software didn't keep pushing the envelope, hardware would never improve or evolve, and we'd all still be running PDP-10 machines from the 1960's.

I'm not saying that there isn't a place for eeking out the utmost useful life of existing hardware, but that place is not on the bleeding edge, latest versions.

If you want to keep doing what you've been doing on your current hardware, then keep using the software you've been using. It's simple really.

---

### Post by kansasnoob on 2012-05-27
> **xebian said:**
> There is an easier way.  Boot a PP netboot and just install the base no desktop just command line.  Upgrade to QQ first and then install your fav desktop.

I doubt that you'll find a QQ non-pae netboot image.

---

### Post by jerrylamos on 2012-06-11
> **xebian said:**
> ...You get the latest applications which I think will run nicely with previous as much as with latest kernel.
precise lubuntu upgraded to quantal running well here:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu quantal (development branch)"
Linux ThinkPad-T40 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:52 UTC 2012 i686 i686 i686 GNU/Linux

Just did sudo apt-get update, sudo apt-get dist-upgrade.  Mostly worked, downloaded all of quantal including 3.4.0-5 generic which requres pae, and should not have installed and didn't.

This is a Pentium M with no pae so "sudo aptitude full-upgrade" keeps trying to install 3.4.0-5 won't work, Y,n,q and the only useful choice is q.  "safe upgrade" picks up changes that will work.

Anyway, running fine, recommended.

Jerry

---

### Post by dino99 on 2012-06-11
run fine here with new kernel


oem@dub:~$ uname -r
3.4.2-030402-generic

---

### Post by jerrylamos on 2012-06-11
> **pressureman said:**
> 
I'm not saying that there isn't a place for eeking out the utmost useful life of existing hardware, but that place is not on the bleeding edge, latest versions.
Well I've got 4 test sysems.  With QQ so far, the only one that runs as is no problem is a netbook.  

The 3.3 Ghz ATI radeon xpress 200 running fine once I figured out I had to use "nomodeset" to boot the startup disk.  Shades of Intrepid for those of us that go back that far, Dapper Drake Beta for me.  Some problems seem to haunt Ubuntu forever.

The widescreen notebook has mucho problems with with wide screen and especially external monitor et. al. something to do with fglrx likely, people are working on it.  It'll do 64 bit I rarely try that.

This is a Thinkpad T40 fits fine on the dining room table, QQ lubuntu running responsively using precise kernel, example of a successful upgrade.

From time to time one or another of my pc's does fall off the bottom:  A 2 GHz with Intel integrated graphics running too slow for me after Intrepid.  A 1 GHz Thinkpad runs O.K. with Lucid rather sluggish with any Narwhal and later.

Now Microsoft is master of "new operating system with lots more overhead, buy it installed on a new faster pc". 

I'm an "ordinary user", internet video, email, research health, news, weather, shopping, politics, sports activities to do...  There's a whole community out there that has to have the very latest hardware gadget and the very latest software to exploit it for the fanciest eye candy and exotic games. They seem to be pretty good at finding and filing bugs.  

Having fun, Jerry

---

### Post by jerrylamos on 2012-06-13
Found another way to use the Pentium M non-pae with Quantal.  Quantal's running on my big clunky widescreen (wide but short screen squint) notebook, and the Pentium M is on the dining room table (much better fit) running ssh -X to the clunky widescreen notebook firefox et. al.

Not sure about the video speed (you tube Shakira) I guess I could put them side by side and compare.

Still having fun.

Jerry

p.s my usual fiddle with Ubuntu Hacks and The Official Notebook plus Ubuntu Wiki to get ssh running wireless security et.al.  Not many commands to get it running, and not sure which ones did the work, and hopefully my neighbor's kids can't log in or view files...and most importantly my wife can still print pictures over the network...
p.p.s. Pentium M's mostly updated from precise to quantal except kernel of course and some other stuff I don't know what is used for.

---

