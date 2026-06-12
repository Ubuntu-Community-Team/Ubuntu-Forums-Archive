---
title: "Continuing gstreamer bad plugin decoding issue (if you have a debian install.."
date: 2012-06-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mc4man on 2012-06-20
Then it would be interesting if the below attached clip can be played in totem or banshee properly

If so or not would be good to know what version of the bad plugin is installed - .22 or .23 (I think sid uses .23

Here is the bug, (complexly ignored) that arose in 12.04 & continues in 12.10 but that's no surprise as the plugin is the same. Whether 12.10 will use the current .22, the .23 or move to gstreamer 1.0 (0.11) I don't know. The 1.0 libs are available but atm can't be used (needs a clutter-gst that's not available

[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014)

---

### Post by mc4man on 2012-06-23
A onetime bump on the odd chancesomeoe has a debian install & a few spare seconds.
Ultimately doesn't matter here much, the plugin is easy to fix locally but I know many affected won't do that & will resort to the less than ideal workaround.

---

### Post by mc4man on 2012-07-25
While the gst-bad videoparser break continues it's meandering ways noticed a related, but separate break in totem-mozilla. It currently won't display AVC or MPEG4 video if in .mp4 or .mov, whether online or locally loaded in a browser like FF

[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1028755](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1028755)

---

### Post by ventrical on 2012-07-25
This was originally a Debian install.

I ran that file .. nothing.

Do I have the right files?

Edit:

Blackspace with Banshee too.

---

### Post by mc4man on 2012-07-25
> **ventrical said:**
> This was originally a Debian install.

I ran that file .. nothing.

Do I have the right files?
The videoparser issue with *some* local AVC files & *some* youtube
vid's thru minitube is from the gstreamer bad plugin. It seems to be a widespread issue inc. the current debian sid bad plugin.
As of yet Debian/Ubuntu, ect. have not upgraded the .10 plugin to the upstream where it has been fixed nor chosen to patch their current bad plugins source to fix, .22 in Ubuntu, .23 in Debian sid

The totem-mozilla issue only affect the 3.4 version of totem & applies to any AVC or MPEG4 in .mov or .mp4

An ex. of online would be here, this should play in firefox but, at least here, produces audio only in the browser window
[http://anon.nasa-global.edgesuite.net/HD_downloads/Arthur_Christmas.mov](http://anon.nasa-global.edgesuite.net/HD_downloads/Arthur_Christmas.mov)

---

### Post by ventrical on 2012-07-25
Still cannot play those files or links. The 1.0 version of gstreamer bad installed through synaptic.

 Sorry I could not be of help.

---

### Post by mc4man on 2012-07-25
> **ventrical said:**
> Still cannot play those files or links. The 1.0 version of gstreamer bad installed through synaptic.

 Sorry I could not be of help.
The 1.0 gstreamer plugins in 12.10 are ATM, worthless. Nothing uses them & it's quite possible 12.10 will not upgrade to gstreamer-1.0 this cycle anyway.
(confirming the totem-mozilla bug Was helpful..

The bad plugin issue with some AVC local files, minitube, ect. in 12.04/12.10/Debian/others is easily fixed, either by a workaround of moving libgstvideoparsersbad.so to a .bak or better - patching & rebuilding the bad plugin.

The totem-mozilla issue with all .mov & .mp4 I don't see a fix for yet other than using the 3.0.1 version of totem* or maybe 3.2.x

---

### Post by philinux on 2012-07-26
Two updates just arrived.

```
Setting up libgstreamer-plugins-bad0.10-0:amd64 (0.10.22.3-2ubuntu3) ...
Setting up gstreamer0.10-plugins-bad:amd64 (0.10.22.3-2ubuntu3) ...
Processing triggers for libc-bin ...
```

---

### Post by mc4man on 2012-07-26
> **philinux said:**
> Two updates just arrived.

```
Setting up libgstreamer-plugins-bad0.10-0:amd64 (0.10.22.3-2ubuntu3) ...
Setting up gstreamer0.10-plugins-bad:amd64 (0.10.22.3-2ubuntu3) ...
Processing triggers for libc-bin ...
```

That won't be fixing this or much of anything else - Ubuntu is still using the .22 version, with a few minor code updates,  which released over 14 months ago.

The commit to fix the parser issue came out on 5/19, (placed a bug with gstreamer a few days earlier & they fixed right away

So neither Ubuntu or Debian is using that yet or ever. ( the 1.0 was also fixed on 5/19 so whenever Ubuntu moves to that the parser will be ok though that won't do 12.04 any good and probably 12.10 also as it seems unlikely to get gst-1.0

---

