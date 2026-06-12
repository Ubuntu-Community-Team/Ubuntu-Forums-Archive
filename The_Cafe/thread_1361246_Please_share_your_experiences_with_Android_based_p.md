---
title: "Please share your experiences with Android based phones"
date: 2009-12-21
forum: The Cafe
---

### Post by legolas_w on 2009-12-21
Hi,

I am looking to buy a Motorola Cliq soon. I am wondering how well cliq (Dext) play with Ubuntu linux in term of synchronizing SMS, MMS, Contacts, TODOs, etc.

Right now I have a windows mobile phone and it has almost no synchronization possibilities with Ubuntu. I keep back up for all of my information in Microsoft myphone service. But there is no such service available for Android.

Thanks

---

### Post by bashveank on 2009-12-21
You don't really need to sync your Android phone with your computer. It automatically syncs with GMail, Google Contacts, Google Tasks, etc.... If you want more (on any platform, not just Linux) you're out of luck. However, I've found that I don't really need anything more than sync with Google apps.

---

### Post by kernelhaxor on 2009-12-21
Android phones are nice.  I'm using myTouch3g right now. 
But I'm not using the stock ROM; I've rooted the phone and installed a custom ROM called Cyanogen.

Android market is really good: thousands of apps for whatever you can think of to do with your phone.
Still Android UI (both OS and most apps) isn't as responsive as the iPhone UI.  I'm not sure if that is due to the hardware but I've noticed that with both G1 and myTouch (don't know about droid).  I've used Iphone 2g, iphone 3g, G1 and myTouch.  
But unlike the iphone, you've a lot more freedom to customize the phone (there are lots of settings).

There's no app to 'sync'.  You can always ssh into your phone and transfer files. So, basically you can sync wireless.

---

### Post by kevdog on 2009-12-21
I have a rooted Moto Droid with the Android 2.0.1 OS.  Basically other than possibly backing up your micro SD card which you need to manually mount -- there really is no synchronization.  One thing however you might need to know if you are in to hacking your phone and installing custom ROMs (as I am).  I don't know if ADB (Android Developer's Bridge) comes in a linux version.  It probably does, but I'm only using the windows variant.  ADB is absolutely essential if you want to mod the phone so its something you want to check out.

Lastly -- if you are into tweaking and are relatively comfortable with the linux command line -- an android phone is for you!  Its really fun to hack things on the phone, and with the nandroid backup utility (similar to a "ghost" image such as on windows), its really easy to restore a working rom after you brick the phone.  You need to install some programs to do this (which take all of 10 minutes), but once you have the foundation set up -- its really fun.  Already released is the upcoming officially released 2.1 ROM and its really amazing!

---

### Post by juancarlospaco on 2009-12-21
*mmm...* if you have SSH you CAN sync...

---

### Post by amitabhishek on 2009-12-21
> **kernelhaxor said:**
> Android phones are nice.  I'm using myTouch3g right now. 
But I'm not using the stock ROM; I've rooted the phone and installed a custom ROM called Cyanogen.


I have been thinking for a while to re-flash my ROM with Cyanogen. I am using HTC magic (Mytouch3G is sold as Magic in India)and am still using HTC's ROM. What performance improvement/difference did you see between both the ROMs. Am I missing something by using manufacturer's ROM? Is Cynogen ROM good?

---

### Post by kevdog on 2009-12-22
Im not sure about cyanogen mods for the 1.x systems, but for 2.x releases, the ssh program is dropbear ssh and not openssh.  Its much smaller and runs faster.   There is an rsync utility also available for 2.x, but to my knowledge (I haven't tried it), it doesnt run over ssh (yet!).  So its possible to do syncs, but not encrypted transfers.  scp is enabled with dropbear as well (or there is an additional program), but there is no sftp functionality (yet!).  I'm not sure what the default system shell is, but I quickly installed busybox to use the ash shell, and I guess there is also available a true bash shell --> however the current implementation breaks ssh with dns lookups (if this is required).  All of this is being worked on, and may be reconciled within the next few days.

Just my opinion of course, but I don't think the need to do a sync is absolutely critical.  All partitions can be backed up using a custom recovery to the builtin sd card.  These files (all in one folder), can then be transferred to computer via usb cable.  

If you need to sync other files other than system files -- well thats another matter.

---

### Post by gnomeuser on 2009-12-22
[My adventures with the HTC Hero](http://davidnielsen.wordpress.com/2009/12/22/why-i-will-be-returning-my-htc-hero/)

---

### Post by legolas_w on 2010-01-04
Hi,

I ordered a Motorola Cliq and I am looking forward to use it.

Thanks

---

### Post by Excedio on 2010-01-04
Does anyone here use the Hero on Sprint's network? What are your thoughts?

---

### Post by bashveank on 2010-01-04
> **Excedio said:**
> Does anyone here use the Hero on Sprint's network? What are your thoughts?

Sprint's a great network, the Hero's a bit underpowered.

---

### Post by skewty on 2010-01-04
I have an HTC G1 (the Rogers Dream actually).

The screen scratches way too easy.  It is slow and studders frequently.
A lot of the apps in Market Place suck and crash frequently.  The v1.5 firmware I am stuck with (Rogers doesn't want to update to 1.6) is too old to run some of the Market Place apps.

The keyboard is pretty good.  I am pretty fast on it now.
The wifi antenna sucks.  You need mini-apps to make it work the way it should as some of the defaults are lame.

That's enough for now </rant>

Scott

---

### Post by amitabhishek on 2010-01-05
I have an HTC Magic. The original firmware sucked big time. It didn't had mail for exchange (a must for me), voice dialling, voice search among others. 

Anyways I used the phone with OEM firmware for about a couple of month. Then I decided to flash the phone with Hero ROM. The eye candy was good but it came with a price: speed. The ROM was too much for the hardware I had. Finally I decided to flash the phone with the much vaunted Cyanogen's ROM and this ROM kicked some serious butt. I got multi-touch, great performance boost, tethering, few bonus apps, root access etc.

In a nutshell if its an HTC's Android phone the ROM gotta be a Cyanogen's :).

---

### Post by scottuss on 2010-01-11
> **amitabhishek said:**
> I have been thinking for a while to re-flash my ROM with Cyanogen. I am using HTC magic (Mytouch3G is sold as Magic in India)and am still using HTC's ROM. What performance improvement/difference did you see between both the ROMs. Am I missing something by using manufacturer's ROM? Is Cynogen ROM good?

I know this was asked a while ago, but I flashed Cyanogen onto my HTC Magic today. It's so much better! The better keyboard alone is worth the update!

As for speed, I'd say it's a little faster (not massively) but the browser is MUCH faster

---

### Post by whiskeylover on 2010-01-11
Any opinions on a GSM based Android phones?

---

### Post by scottuss on 2010-01-11
> **whiskeylover said:**
> Any opinions on a GSM based Android phones?

I've got the HTC Magic (UK) and it's fantastic. To be honest, I'd really like a Nexus One! But my next purchase will be one of the cheap and cheerful 'droid handsets for going on nights out etc.

My friend has the Hero and it's pretty fantastic, the screen quality is top notch!

---

### Post by Cracklepop on 2011-04-05
> **amitabhishek said:**
> I have an HTC Magic. The original firmware sucked big time. It didn't had mail for exchange (a must for me), voice dialling, voice search among others. 

Anyways I used the phone with OEM firmware for about a couple of month. Then I decided to flash the phone with Hero ROM. The eye candy was good but it came with a price: speed. The ROM was too much for the hardware I had. Finally I decided to flash the phone with the much vaunted Cyanogen's ROM and this ROM kicked some serious butt. I got multi-touch, great performance boost, tethering, few bonus apps, root access etc.

In a nutshell if its an HTC's Android phone the ROM gotta be a Cyanogen's :).

I just flashed my Nexus One to CM7(rc4).  
I had 2.3.3 already, and it was great, but the stock Android kernel doesn't have a cifs module, so I couldn't use CifsManager to mount my samba media server share locally (to stream videos to my phone)...:(

But CM has cifs, so it replaced the stock 2.3 tonight, and now I have a wifi window to my home video collection in my pocket :D

I haven't really noticed any significant differences besides cifs and root by default, and the downside is I won't get automatic OTA updates anymore....but if you need a feature from CM, don't hesitate to change!

---

