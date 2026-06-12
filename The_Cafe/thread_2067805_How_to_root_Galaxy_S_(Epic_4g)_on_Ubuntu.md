---
title: "How to root Galaxy S (Epic 4g) on Ubuntu?"
date: 2012-10-07
forum: The Cafe
---

### Post by PuddingKnife on 2012-10-07
I've spent all morning trying to find clear instructions for rooting an original Galaxy S on Ubuntu, with no luck so far. 

So I come to you, Ubuntu Forums, to help guide me toward the bliss of having a rooted Android phone. 

It is my goal to root my Galaxy S and install Jelly Bean onto it to give it an extended life. 

Please, please help!

---

### Post by mamamia88 on 2012-10-07
check out the xda forums for your phone and take a look at [http://forum.xda-developers.com/showthread.php?t=1076967](http://forum.xda-developers.com/showthread.php?t=1076967)

---

### Post by PuddingKnife on 2012-10-07
Well, I did, and found this:

[http://forum.xda-developers.com/showthread.php?t=788490&highlight=root+ubuntu](http://forum.xda-developers.com/showthread.php?t=788490&highlight=root+ubuntu)

...but I have no idea what to do with it. I made the files executable and ran the script in the terminal, but it didn't really work out. 

So, as a last resort before I throw this thing out the window, was to inquire if anyone around HERE has had any success rooting the phone using the OS of choice around these parts.

---

### Post by mamamia88 on 2012-10-07
you running gingerbread?

---

### Post by AllRadioisDead on 2012-10-07
I don't know much about the Epic 4G, but every Samsung phone I've ever owned has been rootable by installing a custom kernel with Odin. In the case of Ubuntu, Heimdall or whatever it's called is probably going to be your go to software.

---

### Post by PuddingKnife on 2012-10-08
> **mamamia88 said:**
> you running gingerbread?

Yes.

> **AllRadioisDead said:**
> I don't know much about the Epic 4G, but every Samsung phone I've ever owned has been rootable by installing a custom kernel with Odin. In the case of Ubuntu, Heimdall or whatever it's called is probably going to be your go to software.

Interesting, so you can install a custom kernel w/o having to root it? I have already have Heimdall installed so this development could be helpful. Thanks

---

### Post by mamamia88 on 2012-10-08
> **PuddingKnife said:**
> Yes.



Interesting, so you can install a custom kernel w/o having to root it? I have already have Heimdall installed so this development could be helpful. Thanks

says specifically in that post that it doesn't work in gingerbread.  can you downgrade?

---

### Post by fontis on 2012-10-08
It's quite easy to root them. You essentially need to flash the phone with a custom kernel. The kernel needs to work with your specific gingerbread build e.g. XXJVH or whatever it may be. 
The easiest way to do it is to just flash a custom rom and kernel all in one basically. 

A good rom to flash is the CyanogenMod. I'm using it on my own SGS (but mind you I dont' have the Epic 4g)

---

### Post by PuddingKnife on 2012-10-08
> **mamamia88 said:**
> says specifically in that post that it doesn't work in gingerbread.  can you downgrade?

I don't know how to downgrade, but thank you for your patience so far. 


> **fontis said:**
> It's quite easy to root them. You essentially need to flash the phone with a custom kernel. The kernel needs to work with your specific gingerbread build e.g. XXJVH or whatever it may be. 
The easiest way to do it is to just flash a custom rom and kernel all in one basically. 

A good rom to flash is the CyanogenMod. I'm using it on my own SGS (but mind you I dont' have the Epic 4g)

So, is there a guide somewhere for that? I currently have Heimdall and Heimdall-frontend installed, but from there is where I'm getting lost.

---

### Post by fontis on 2012-10-08
Well heimdall is the program you use to flash the firmware onto the phone. If you have that sorted already then the nextstep is to get the firmware to flash :)

Check [http://forum.xda-developers.com](http://forum.xda-developers.com) for your specific device, theres tons of ROM's and information there.

Another website for a ROM is [www.cyanogenmod.com](www.cyanogenmod.com) 
Find your device and flash the Stable version. There's also a wiki there to explain the steps that you cover when you flash.

Personally I've never flashed using Ubuntu, I've only flashed via Odin in Windows, but then again the computer I had working didn't have any Ubuntu install but it should be similar. 
Goodluck

---

### Post by PuddingKnife on 2012-10-08
Sweet, thank you for your help. My main issue so far has been finding guides or videos detailing how to flash a ROM onto your phone almost invariably start with "Great, now that your phone is rooted and you have CWM Recovery installed, we do the flashing now!"

My problem is that the tools to accomplish the rooting on Ubuntu are few and far between. Almost as rare as clearly defined directions for Ubuntu users. I think if I had a Windows box I would be running Jelly Bean by now lol.

Thanks again

---

### Post by fontis on 2012-10-08
Hehe, Google is your friend bro!

But really, I can personally recommend Cyanogenmod. It's the most popular custom ROM out there and it works on a great variety of devices. It's basically a "vanilla android" without all the crap that manufacturers throw in sometimes.

For me (using SGS I9000) it's great, fast, stable, and the ONLY way I can run Android 4.x since Samsung refuses to update these devices.

And for the record, Heimdall and odin are essentially the same thing. I'm sure there's guides out there explaining how they work out. For me, Odin makes more sense (but the interface is fubar unless you're used to it) but that's mainly because that's what I'm accustomed to. But I've flashed using heimdall in Windows and from what I gather it's the same in Ubuntu, (and it was pretty straight forward as well - in fact I flashed CM9 using Heimdall)

---

