---
title: "Zoneminder and ubuntu server 12.04"
date: 2013-09-01
forum: Server Platforms
---

### Post by remush on 2013-09-01
Hi all,

I'm trying to setup a webcam with ubuntu server 12.04 as a motion sensitive security camera.

I've been trying to do this for over a week and have had no luck.

lsusb reports webcam as :  046d:0928 Logitech, Inc. QuickCam Express

other info
lsmod | grep videodev : videodev               86588  2 gspca_main

I'm not too good at linux, I am going to need some help with this.

Thanks.

---

### Post by TheFu on 2013-09-01
Well, what have you tried?
What failed ... exactly?  Please copy/paste commands + errors.

Were you following a "how-to" from some where?  I googled "ubuntu 12.04 zoneminder" and the top returns seemed pretty good, but I've never tried this myself.  The zoneminder wiki has a how-to - it seemed like they were doing many things the hard way, but .... whatever. Ought to work.

Linux is like learning a new language. Some things are the same, many things are completely different.  Just like trying to learn Chinese, having a few words is helpful, but you can't really understand what the other guy is saying. Linux is sorta like that until you go native, intensive study for 1-2 months. Live it.

---

### Post by houstonbofh on 2013-09-02
I have used zoneminder many times, and I am also not sure what you are asking.

Also, you might have better luck on the ZoneMinder forums.  [http://www.zoneminder.com/forums/](http://www.zoneminder.com/forums/)  Then generally have a better idea of how to support odd hardware.

However, here are some links that may help.
[http://www.zoneminder.com/wiki/index.php/Logitech_QuickCam_Express](http://www.zoneminder.com/wiki/index.php/Logitech_QuickCam_Express)
[http://www.zoneminder.com/wiki/index.php/Hardware_Compatibility_List#USB_Cameras](http://www.zoneminder.com/wiki/index.php/Hardware_Compatibility_List#USB_Cameras)

---

### Post by remush on 2013-09-03
Sorry my post was so confusing, I think I'm very frustrated.

Logitech Quickcam Express that I have does not work on ubuntu 12.04
I followed every google tip i could find online, and nothing worked. Sorry but I am un motivated to search for them all again, and past links.

I ended up installing Ubuntu server 10.04 and go the camera working with a patch, however the same patch does not work with ubuntu server 12.04

BUT ubuntu server 10.04 only supports zoneminder up to 1.24.2 which has bugs, to which i've found no full working patch, only partial patch'es that still leave the system with problems. Also it will not generate video's from recordings.

I've been posting to the zoneminder forum, but have not had any good leads yet. The bugs i'm talking about are well known on the zoneminder forums, but there has never been a solution. the bugs persist in ubuntu server 11.10 as well.

no drivers = stress

I'm going to try other software for the time being, thanks to all help :)

---

### Post by scbingham on 2013-09-04
Cheese is an excellent program to test that web cams will work with Ubuntu.

Have you had a look at Motion? I haven't actually set it up yet but on comparison it looks easier to set up than Zoneminder.

Hope that's of some help.

---

