---
title: "Need help getting TF2 working in Steam with Wine..."
date: 2009-07-17
forum: Wine
---

### Post by TF2-Engi on 2009-07-17
I have steam and wine installed now I want to install Team Fortress 2 and getting that working.  I need help please, if anyone could help it would be greatly appreciated!!!  Thanks!

---

### Post by PureLoneWolf on 2009-07-17
I had all sorts of problems installing TF2 through Wine.  In the end I used my Virtualbox XP, installed steam on a partition that Wine could access when the Virtualbox was not running, installed TF2 there and then when I launched Steam, I had the option to run TF2.

You may need to specify some code in the launch options for TF2 (I did)

```
-windowed -width 1280 -height 1024 - heapsize 2097152 -dxlevel 80
```

-windowed as I have twinview
-width/height for my preferred resolution
-heapsize is half of my system ram
-dxlevel 80 stopped me getting random crashes

Hope that helps some

---

### Post by TF2-Engi on 2009-07-17
> **PureLoneWolf said:**
> I had all sorts of problems installing TF2 through Wine.  In the end I used my Virtualbox XP, installed steam on a partition that Wine could access when the Virtualbox was not running, installed TF2 there and then when I launched Steam, I had the option to run TF2.

You may need to specify some code in the launch options for TF2 (I did)

```
-windowed -width 1280 -height 1024 - heapsize 2097152 -dxlevel 80
```-windowed as I have twinview
-width/height for my preferred resolution
-heapsize is half of my system ram
-dxlevel 80 stopped me getting random crashes

Hope that helps some

How do you get virtualbox XP working?  Thanks, sorry I am a total novice at this, I have had windows my entire life...

---

### Post by PureLoneWolf on 2009-07-18
Hi again

Did you dual boot your Ubuntu setup?  Meaning, are you able to launch Windows at all?

If yes, that is the easiest method - Boot into Windows, install steam and TF2, boot back into Ubuntu and use wine to run the copy of Steam.

If you can't get into windows, you need to install virtualbox (there is a USB-less version in the repos) - Check the "Synaptic Package Manager" and search for virtualbox.

Once that is installed, you will need to setup a machine within it and install XP

---

