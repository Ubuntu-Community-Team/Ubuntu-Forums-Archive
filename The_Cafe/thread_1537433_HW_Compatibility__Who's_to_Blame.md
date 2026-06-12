---
title: "HW Compatibility:  Who's to Blame?"
date: 2010-07-23
forum: The Cafe
---

### Post by McRat on 2010-07-23
At 5:00am after working at it all night after my "real job" I found proof of the Black Helicopters Attack Squad in a 5 year old LCD monitor.
 
As a few have noticed, there are video driver problems with a large number of monitors that have native 1440x900? resolution...
 
"DUDE! This worked GREAT with Windows! It doesn't work with the Linux ATI/nVidia Driver!!"
 
Who is to blame? Not the Linux people, not the Windows people, not the Monitor people, perhaps not even the Video people. Some of the blame is with the Computer Maker.
 
First let's settle up some myths: Windows XP runs hardware better than Ubuntu Linux. 
 
No. If you build a brand new computer from scratch with the latest parts, and DO NOT have the Motherboard MFR CD-ROM, a new 2010 XP SP3 shrinkwrapped disc install will not see squat. It won't see the video card, network card, sound card, etc. It can't even hook to the network to get drivers. For real. NO NO! Not the Computer MFR disc, a WINDOWS disk.
 
That difference is the issue. The computer MFR disc does NOT necessarily have the same drivers that the public can get.
 
I took a new Clone (MSI-AMD-ATI build) and loaded Ubuntu on it with NO drivers. Everything worked. EVEN THE MONITOR at 1440x900 and 75hz refresh...
 
Loaded the video driver from Video MFR, and the monitor would not support 1440x900 at the correct 75hz refresh. (Could not see 10% of the screen).
 
Now I started again with a new WinXP SP3 disk. Out of the box, it supported the mouse, keyboard, DVD drive, Hard Drive. It did not support the video over 1280x1024 or sound at all.
 
Loaded the video driver from the Video MFR. No 1440x900x75hz either.
 
Now, I removed the Video MFR driver and used the Mobo CDROM, and guess what? Now the monitor is supported.
 
Now the Black Helicopter Theory: When a Computer MFR or Mobo MFR creates a new product, they get extra support from the Video MFR to customize the settings to put into the install disc. These drivers are NOT necessarily the same as what you can get from the Video MFR site. And I also theorize that this same thing is true for the rest of the hardware. It is also highly likely that these "special drivers" are proprietary to the Computer MFR, NOT the Video MFR. "This is OUR custom driver per NDA (Non Disclosure), do not give it to our competitors." Dunno if that's true, it could just be gross incompetence by both ATI and nVidia at the same time.
n
Why do I make such a Jump? They made MILLIONS of these 1440x900 monitors. They came with new systems like HP and Dell. Why would BOTH ATI and nVidia break compatibility the same way?
 
In any case, in this system build, Linux == Windows + Special OEM-only Drivers. Linux > Windows + Public Drivers. And Linux compatibility by itself is far better than the newest XP.
 
I considered doing the test again with a Win7 Disc, but that stupid "YOU'RE A CROOK" crap irritates me too much.

---

### Post by McRat on 2010-07-23
Cliff Notes:  The drivers a Computer MFR provides with a system are better than what you can get in public.

---

### Post by spoons on 2010-07-23
All HD Audio codecs built into the motherboard use a generic driver from Microsoft and they work out of the box on Vista and 7. Windows 7 also picks up my graphics card and network card OOTB.

I think what is to blame is a lack of standardized interfaces on Linux. If a graphics card manufacturer makes a graphics driver, it probably won't work with the new Ubuntu in 6 months time because things are changed. Windows drivers on release still work on the service pack'd beefed up version. (this is also helped by less frequent releases of Windows)

Also, even if it's on the manufacturer's disc, this is still a driver. There is still a driver for Windows, and not for Linux. I don't think most people care about freedom or alternatives or all that guff - they just want it to work and if it doesn't work it's no good to them. I understand this is the case for certain specific pieces of hardware. I'm glad Ubuntu worked well OOTB on your system. But for some of us it doesn't, and we'll carry on using Windows until it does, or until we have the motivation to fix it ourselves.

---

### Post by McRat on 2010-07-23
> **spoons said:**
> All HD Audio codecs built into the motherboard use a generic driver from Microsoft and they work out of the box on Vista and 7. Windows 7 also picks up my graphics card and network card OOTB.
 
I think what is to blame is a lack of standardized interfaces on Linux. If a graphics card manufacturer makes a graphics driver, it probably won't work with the new Ubuntu in 6 months time because things are changed. Windows drivers on release still work on the service pack'd beefed up version. (this is also helped by less frequent releases of Windows)
 
Also, even if it's on the manufacturer's disc, this is still a driver. There is still a driver for Windows, and not for Linux. I don't think most people care about freedom or alternatives or all that guff - they just want it to work and if it doesn't work it's no good to them. I understand this is the case for certain specific pieces of hardware. I'm glad Ubuntu worked well OOTB on your system. But for some of us it doesn't, and we'll carry on using Windows until it does, or until we have the motivation to fix it ourselves.
 
Yeah, I didn't test Vista or Win7. Since they don't run the work software I need to run, I would be just testing them "fun" only.
 
But I might bite the bullet and see what Win7 does on a machine it was not designed to run on without the OEM drivers to see if you're right.  My first effort got random crashes during read/writes, but that was probably a fluke.

---

### Post by McRat on 2010-07-23
> **spoons said:**
> .. There is still a driver for Windows, and not for Linux. I don't think most people care about freedom or alternatives or all that guff - they just want it to work and if it doesn't work it's no good to them. I understand this is the case for certain specific pieces of hardware. I'm glad Ubuntu worked well OOTB on your system. But for some of us it doesn't, and we'll carry on using Windows until it does, or until we have the motivation to fix it ourselves.

Here's something I don't get.  Why would you switch operating systems if the one you have does what you want?

While I now have 5 systems running Linux, I never replaced a Working With Windows machine's OS.  It was either a new build or "Linux or Dumpster". 

There are two paths:

"If it ain't busted, don't fix it."

or

"Fix it till it's Busted, then fix it some more."

One path is the path of least resistance, the other, a hobby or obsession.


For me, Linux is a "fix" for something that is busted, not a leisure-time hobby.  Although I'm thinking about second option...   :D

---

