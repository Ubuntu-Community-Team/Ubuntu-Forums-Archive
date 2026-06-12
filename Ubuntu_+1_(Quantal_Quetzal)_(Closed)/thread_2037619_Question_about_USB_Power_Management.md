---
title: "Question about USB Power Management"
date: 2012-08-05
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-08-05
I have noticed, in the last week or so, my wireless stuff that have USB Transmitters/Receivers (Logitech Mouses/Touchpad, Microsoft Keyboard, Headset) were acting a little strange.

This is in a Desktop.

- The mouses: When the Desktop was left alone for a while and I would start using it again, the mouse arrow wouldn't move immediately. It takes between a second or two and then it would work normally.

- Keyboard: Nothing would show on the screen for 1-2 seconds, then the word(s) I typed would show at once on screen.

- Headset: Sound wouldn't start immediately when I pressed play on YouTube, and a problem with audio/video sync started to get very annoying. 

Being the moron that I am, I somehow decided that I had a problem with radio interference and practically destroyed my home and work infrastructure looking for it. 

Then I thought about the obvious (power management). I know nothing about it, much less in a desktop. But I went to /sys/bus/usb/devices/<USB Devices of the transmitters>/ and wrote "-1" to the "autosuspend" files (according to the documentation I found at [http://lwn.net/Articles/253587/](http://lwn.net/Articles/253587/)

Guess what: Things are snappy again, no more delays to start working after a pause. 

So, is anyone familiar with current Power Management methods and policy, including USB port, for Desktops? Despite the Green IT spirit, I don't get why the OS would sleep a USB on a Desktop (not a laptop), unless you were running on a UPS or something.

Regards,
Effenberg

**EDIT:** I found out that powertop on PP on a ASUS laptop does the same if you accept all of its suggested power improvements. Then if you disable management for the specific USB ports, wireless mouses and devices work normally again (no sleep/wake delay).

---

### Post by ronacc on 2012-08-05
I just installed an HP wireless keyboard/mouse on a DT running maveric out in my workshop to replace my logitec  ( a rat chewed the mouse ) and it does the same thing . I wonder if the system wrote a new file for that device and used the defaults ? I had everything set to "never" before . I'll investigate later and report back .

---

### Post by VinDSL on 2012-08-05
> **effenberg0x0 said:**
> I have noticed, in the last week or so, my wireless stuff that have USB Transmitters/Receivers (Logitech Mouses/Touchpad, Microsoft Keyboard, Headset) were acting a little strange.[...]

I went to /sys/bus/usb/devices/<USB Devices of the transmitters>/ and wrote "-1" to the "autosuspend" files (according to the documentation I found at [http://lwn.net/Articles/253587/](http://lwn.net/Articles/253587/)

Guess what: Things are snappy again, no more delays to start working after a pause.[...]

> **ronacc said:**
> I wonder if the system wrote a new file for that device and used the defaults ? I had everything set to "never" before [...]
Had a similar problem with the built-in web cam in my lappy.

After I first booted, the web cam would work fine in Skype.  But, after I let the lappy sit for a while, it would suspend power to the USB ports.

When the lappy awoke from its slumber, everything would come back except the web cam.  Skype said the web cam was in use by a different program.  Only way to get it working again was to restart (warm boot).

Turned out, the integrated web cam was running off of the USB circuit.  Setting USB power suspension to "never" took care of the problem.

---

### Post by ronacc on 2012-08-05
all I have to do to get my mouse back is click a button ( scrol wheel won't do it ) .

---

### Post by effenberg0x0 on 2012-08-06
I have always preferred using desktops to laptops, so I never took the time to really understand the Power Management stuff. I did study upower a little last cycle and have used powertop a couple times and that's it.

My questions right now are:
- Desktops:  Is sleeping USBs really important and desirable on machines that are fed by AC current and 500W+ PSUs? I could understand this being activated on a power loss, when the equipment is running on PSU batteries. 

- Workstations: Talking to a friend about this, he mentioned an Ubuntu desktop that slept the USBs when they were away from the lab overnight. The only problem is that the USB was connected to expensive medical equipment doing biological material analysis (data logger). I have worked with telecom equipment (RF, Satellite, etc) that connects to USB too. I own a USB oscilloscope and I have used it to measure circuits for long periods and log. People who use these sort of equipment generally will connect the USB cable to desktops/workstations, not laptops, because there's no interest in mobility. You generally buy/build a reliable Desktop/Workstation for science application (dual PSU, ECC memory, 4+ HDD in RAID, maybe a Quadro Card, etc). There's absolutely no interest in sleeping anything. I can tell you, from my own experience, that in health and pharmaceutical, engineering, telecom, financial, stock and credit analysis systems, oil, gas & mining, security and automation, defense, and other fields, there's absolutely no chance to have desktops sleeping stuff at will. 

- Laptops: If the thing decides to sleep a webcam or a headset during a business videoconf, or slide controller during a presentation, it can become a serious problem. But I can sort of understand the need to save battery. As long as we could setuo what will be disabled and when.

- PCs in General: Summarizing, how does the system define that it is safe (and not counterproductive) to sleep certain USBs? 

I think its absolutely essential to have completely reliable and accessible, very comprehensive and detailed, GUI settings for power management as a system default in g-c-c then. Or make it clear for professional users that plan to adopt Ubuntu that the machine is unreliable when it comes to the way it handles powering it's internal / external devices (or that there's no easy/ordinary-user-friendly way to set this).

Or is this a bug rather than a design choice? As in "because of latest changes to Linux kernel, Ubuntu is now sleeping everything after n milliseconds no matter what and we need to fix it"?

Regards,
Effenberg

---

### Post by ronacc on 2012-08-06
If its a bug it's been around for awhile  that box in my workshop I mentioned earlier is running 10.04  .
You are right about a comprehensive GUI  .

---

### Post by VinDSL on 2012-08-06
> **effenberg0x0 said:**
> My questions right now are:
- Desktops:  Is sleeping USBs really important and desirable on machines that are fed by AC current and 500W+ PSUs? I could understand this being activated on a power loss, when the equipment is running on PSU batteries. 

- Workstations: Talking to a friend about this, he mentioned an Ubuntu desktop that slept the USBs when they were away from the lab overnight. The only problem is that the USB was connected to expensive medical equipment doing biological material analysis (data logger). I have worked with telecom equipment (RF, Satellite, etc) that connects to USB too. I own a USB oscilloscope and I have used it to measure circuits for long periods and log. People who use these sort of equipment generally will connect the USB cable to desktops/workstations, not laptops, because there's no interest in mobility. You generally buy/build a reliable Desktop/Workstation for science application (dual PSU, ECC memory, 4+ HDD in RAID, maybe a Quadro Card, etc). There's absolutely no interest in sleeping anything. I can tell you, from my own experience, that in health and pharmaceutical, engineering, telecom, financial, stock and credit analysis systems, oil, gas & mining, security and automation, defense, and other fields, there's absolutely no chance to have desktops sleeping stuff at will. 

- Laptops: If the thing decides to sleep a webcam or a headset during a business videoconf, or slide controller during a presentation, it can become a serious problem. But I can sort of understand the need to save battery. As long as we could setuo what will be disabled and when.

- PCs in General: Summarizing, how does the system define that it is safe (and not counterproductive) to sleep certain USBs? 
IMO, with the exception of "portables" (in very specific situations) "power saving" so called is minimal.

I don't how it is in your country, but there is a AC power receptacle on every wall in America.  You cannot walk 20 feet without finding another wall plug. I carry a battery around in my laptop case, but seldom use it, so "power saving" doesn't mean jack, to me.

The only time "power saving" is important is when I'm on a long (airplane) flight, and I *need* to get some work done -- like typing up proposals, and so forth.  Or, when I'm typing notes on one of those convention tables, at a workshop or whatever, where the nearest wall is 100 feet away.

In the case of USB ports, I don't *think* it turns the power off anyway.  For instance, I always use a USB-powered "lap cooler".  This "lap cooler" NEVER stops running when my laptop/netbook are powered-up, even if they go into sleep mode.

Regarding workstation/desktop machines, all I have to go by is ancient iron.  My machines, here at the abode, are circa 2000-2006.  I've hooked up a "P3 Kill-A-Watt Meter" to them, and monitored their power usage.  Enabling all of the "power saving" features doesn't save jack.  The machine I'm typing this on (see my sig for details) uses 200+ watts 24/7 regardless of its "power saving" state.

In "mission critical" situations, I would (and do) turn off all this "power saving" nonsense.

For general computing, I enable some "power saving" features simply because I like to watch the screensaver do its thing.  LoL! :D

---

### Post by kurt18947 on 2012-08-06
> **ronacc said:**
> I just installed an HP wireless keyboard/mouse on a DT running maveric out in my workshop to replace my logitec**  ( a rat chewed the mouse ) **
<snip>


You need a cat :p (or rat terrier).

---

### Post by ronacc on 2012-08-06
I've got a lab puppy but at this stage (the chew everything in sight stage ) she's more destructive than the rats .

---

### Post by VinDSL on 2012-08-06
That's funny!

I saw a dead rat, in the parking lot, last week.  Ants were "chewing" it up.

Also, later that week, I saw a rat ran in the front door of a CVS Pharmacy.  Man, did that freak ppl out!?!?!

I don't know why I'm telling you this, but it's yours for free.  LoL!  :D

---

### Post by cariboo on 2012-08-06
On my desktop system, I noticed the MS wireless mouse keeps trying to communicate with the transceiver, when the system has seemingly gone into power saving mode. The mouse flashes periodically, when the system is in power saving mode or shut down completely, this may have something to do with the mouse, as it doesn't seem to go through batteries any quicker than previous MS wireless peripherals I've owned.

---

