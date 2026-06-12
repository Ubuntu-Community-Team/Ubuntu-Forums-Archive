---
title: "Installation/Reboot Issues"
date: 2015-11-19
forum: Server Platforms
---

### Post by Benjaman_Woolner on 2015-11-19
I'm not sure what the culprit is that is currently causing my issues. I previously posted on here having issues getting Ubuntu Server to install on my pc, but thought I had finally made a break through. (see original post here: [http://ubuntuforums.org/showthread.php?t=2303305](http://ubuntuforums.org/showthread.php?t=2303305))

Having been able to log in I was happy that all must have installed correctly, but as it was late in the day I decided to shut the pc down using "sudo shutdown now" especially as I hadn't done anything other than install Ubuntu Server and logged in.

Now when I come to restart I get a plain black screen, again with no cursor. I decided to insert my flash drive and try to run a boot repair and see if I could fix any issues that may be there.

On trying this I was presented with a screen that gave me the following information

mount: mounting /dev/sda on /media failed: Invalid argument
unmount: can't unmount /media: Invalid argument
mount: mounting /dev/sda on /media failed: Invalid argument
mount: mounting /dev/sdb on /media failed: Invalid argument
unmount: can't unmount /media: Invalid argument
mount: mounting /dev/sdb on /media failed: Invalid argument

It sat like that for a couple of minutes and then took me to the screen to try and setup up my keyboard location. This is strange as I believe it was a similar issue that I had when initially trying to install Ubuntu Server. It came up with a similar issue of mounting/unmounting but I didn't catch the location, then after a little bit it came up allowing me to setup my keyboard location.

Any idea what's going on here? Is there a way ensure the entire install happens on my HDD and not my flash drive?

---

### Post by volkswagner on 2015-11-19
If you've done nothing but install, I suggest reinstall.

May I ask why you're not using a CD for the install?
Why are you using the alternate .iso?

Also if version 14 isn't missing something you need, I suggest using long term release 14.04.x server edition.

A clean install should not need anything mounted at /media.

Let me say this, you can get unexpected results when using USB as install media. There are many threads throughout the
years with oddities, various thumb drives not working at all, while others are fine. It just adds a potential problem to the mix.

---

### Post by Benjaman_Woolner on 2015-11-20
Hi Volkswagner, In answer to your question I was hoping not to use CD's hoping for an easier install plus I'm not entirely sure how well the old disk drive would work.

I initially tried to use 15.10 but was having issue after issue, partly it seems due to the MD5 check failing. I thought trying an older version would help with driver support etc so the version installed was actually 14.04LTS 32bit.

Would I be right to interpret you would recommend burning a copy to CD(s) and see what difference that makes. I guess as least then it rules out trying to save to the wrong location.

---

### Post by volkswagner on 2015-11-20
Yes, I would burn the 32bit server .iso and install from there.

---

### Post by Benjaman_Woolner on 2015-11-25
Ok just to finish up this thread, I burnt a copy of Ubuntu Server 14.04 LTS 32 bit onto a disc and that seems to have done the trick as far as installation is concerned. I guess despite specifically setting up and using only the partitions on the HDD and installing the grub to SDB there still seemed to be some sort of clash between the HDD and the flash drive which the CD install seems to have negated.

---

