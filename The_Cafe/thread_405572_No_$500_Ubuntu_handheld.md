---
title: "No $500 Ubuntu handheld?"
date: 2007-04-09
forum: The Cafe
---

### Post by McLogic on 2007-04-09
Why can't I get a well-built x86 handheld with good battery life for $500 or less?

Nokia builds a fine handheld with a chip that cost just a bit less and uses just a bit less power then the x86 options. They charge about $400 for the device, but it can't run standard Linux and it only has 128 Mb of RAM. It also can't run all the standard Linux x86 stuff from the closed-source guys (Adobe, MS, etc.) It also has no powered USB port.

So the PepperPad (version 3) is nice, but it has a few flaws. I would list them as size, cost, battery life, software, and finish. This sounds like a long list, but it is not. The basics of the device are well chosen: power-efficient x86, 12 volt input, bluetooth, wifi, camera, upgradable RAM, touchscreen, keyboard, hard disk, programable remote control.

The device is too expensive, is too wide, runs outdated Linux, and has poor battery life. To make it less wide, it should go from a hardware keyboard to a translucent on-screen keyboard and from a front-stereo to a rear-mono speaker. To cut the costs, the device should get thicker -- so that the circuit board can get smaller. This thickness should also be used for a larger battery.

A tiny embedded computer with the same 500 MHz Athlon-like x86 with a shared-memory graphics core need not be expensive. A 70 x 60 mm (2.5 x 2.3 inches) computer with 256 Mb of RAM and 512 Mb of flash is around $120 (CM-iGLX). It has pin-outs for almost everything: IDE, 3x USB, PCI, Video Out, Video In, Touchscreen, Speaker, Microphone, Ethernet, etc.

[http://linuxdevices.com/news/NS9996942590.html](http://linuxdevices.com/news/NS9996942590.html)
[http://www.nokiausa.com/n800](http://www.nokiausa.com/n800)
[http://www.hanbitamerica.com/](http://www.hanbitamerica.com/)
[http://www.umpcportal.com/modules/news/article.php?storyid=310](http://www.umpcportal.com/modules/news/article.php?storyid=310)

Why not put a 1.8" zif hard-drive spot under the battey (where Nokia puts SIM cards)? Add this to the video-in, you could make it a Tivo that you can take with you.

---

### Post by macogw on 2007-04-09
You could get a proper laptop with a real keyboard for that much!

Have you seen the OpenMoko?  It's open platform, Linux, uses apt...supposed to compete with the iPhone

---

### Post by Anthem on 2007-04-10
> **macogw said:**
> You could get a proper laptop with a real keyboard for that much!

Have you seen the OpenMoko?  It's open platform, Linux, uses apt...supposed to compete with the iPhone
Yeah, OpenMoko's going to be cool.

Specs are here:

[http://openmoko.com/press/index.html](http://openmoko.com/press/index.html)

But they're not shipping machines yet, or if they are they're only developer boxes.

---

### Post by beefcurry on 2007-04-10
I couldn't wait for the OpenMoko, brought a Dopod 838pro instead. Wish it ran linux but it ran windows mobile.

---

### Post by McLogic on 2007-04-11
> **macogw said:**
> You could get a proper laptop with a real keyboard for that much!

Yes, but that is not what I want. I have a laptop.

I want a communicator/media player that is cargo-pocket sized and is durable. I want to use it in places where I can't put a laptop down. I will make compromises to get the price and size down, like no pen silo and a mono speaker.


> **macogw said:**
> Have you seen the OpenMoko?  It's open platform, Linux, uses apt...supposed to compete with the iPhone

I must have not made myself clear...

I don't want to FLUSH money down the toilet on:
[LIST]
[*]ARM-based hardware that is slow and gets orphaned (Psion)
[*]OMAP/ARM hardware that is slow and gets orphaned (Nokia 770)
[*]x86 hardware that can't use standard Linux or Apps (PepperPad3)
[*]s3c2410 hardware can't use standard Linux or Apps (OpenMoko)
[*]Anything that puts me in an application ghetto (odd window manager, etc)
[/LIST]

What I want is to run an off-the-shelf x86 Linux on the handheld (ubuntu or xubuntu). I don't want the OpenMoko -- it is cool, but not for me. The "open" is useless in 9 months when the vendor moves on unless I want to pick up development. 

I just want a 7" display that does what the UMPCs do, but is stripped down and free of the MS tax. It can have a WVGA screen (850x480) that can run a scaled 1024x567 or 1024x768 (like most UMPC). It can use an translucent on-screen keyboard to get rid of the need for handwriting recognition. A video-conferencing camera should be included.

You can get
[list]
[*] the board (with CPU/GPU/RAM/FLASH/Ethernet/etc) for $120
[*] a screen for $60
[*] lithium ion battery for $100 (2 x $50 flat 3.7v)
[*] 2 Gig SD cards are $15
[/list]

All you need to add is the ports (pinouts are on the board), voltage regulator, charger, and case to get a live-CD-sized Linux device (512 of flash on the board). User files and user-installed programs could go on SD memory cards (have 2 slots like Nokia's n800),  

A 1.8" ZIF-connector hard drive could be an option, but would add $100 and kill battery life.

Also see the links above.

[http://www.osddisplays.com/product_press_releases.php](http://www.osddisplays.com/product_press_releases.php)

---

### Post by matthekc on 2007-04-11
i meet a guy who could take old laptop motherboards strip them down and build what you want but he charged a lot so i didn't keep touch.  He just took small boards took stuff off and made it work and had someone else fab the case.  If you had a micro board a laptop battery, an ipod like hard drive and some killer skills you could make a howto.  There are plenty of really small boards some retail its the display, keys, layout, and case that is hard really.

---

### Post by DoctorMO on 2007-04-12
> hardware can't use standard Linux or Apps

Let me make this QUITE clear to you, Adobe/Macromedia, MS or any other closed source "guys" do NOT make ANY standard linux programs; if their not open source then their non standard, sub standard and about as unstandard as you can get.

Don't ask for something or the reasons why something isn't so when your view is all warped. I don't care if you use those apps or plugins a lot, tough luck, should have thought of that before counting on closed source products.

No sympathy for your unreasonably defined plight.

Further since linux compiles on almost every chip made that the gnu tools compile on your going to find it hard pressed to not be able to find working ports of all real standard and important foss applications.

---

### Post by McLogic on 2007-04-12
**If I can summarize DoctorMO's argument:**
Linux works on all chips if you compile it yourself. Therefor, you don't need an x86 handheld unless you are an MS/Adobe suck-up.

**My response:**
Linux works well on x86, and needs custom development and compiling to be fully-working on other platforms (_power management_, working Flash player, etc). We don't want to make Linux look bad by having people see anything less then Ubuntu in all its glory, and regular users are not interested in compiling software.

Also:
The avalible Linux handhelds are slow, and starved for memory. This is about handheld computers, not FOSS holy-wars. Working is good, and non-working is garbage.

*--> long & rude version follows <---* 

> **DoctorMO said:**
> Let me make this QUITE clear to you, Adobe/Macromedia, MS or any other closed source "guys" ...

The standard that I'm most interested in is the pre-compiled programs from the Ubuntu repositories. I also know that lots of people use w32codex, or applications that don't compile right on non-x86. 

> **DoctorMO said:**
> Don't ask for something or the reasons why something isn't so when your view is all warped. I don't care if you use those apps or plug-ins a lot, tough luck, should have thought of that before counting on closed source products.

Thank your for the sermon, your Holiness. 

Now how are you going to replace a working web browser with a sermon? 

Just try to tell someone that the web browser works when that can't reliably watch U-Tube with working sound. They will not be interested in your holy war.

Linux now works with ACPI power management, but these non-x86 chips use their own power management API's. If you don't program for their non-standard power management, you will have a device that has a really short battery life.

> **DoctorMO said:**
> No sympathy for your unreasonably defined plight.

Further since linux compiles on almost every chip made that the gnu tools compile on your going to find it hard pressed to not be able to find working ports of all real standard and important foss applications.

Users don't want to compile, and everything you might need is already compiled for x86. **Just look at the trouble with x86-64** before you act like it is working and easy. Ubuntu is all about making Linux easy for everyone, even people who can compile. Most regular users can't.

I switched from a mix of Debian & Mandrake to all Ubuntu systems, just because I didn't want to hunt down options and then recompile packages (and do it again and again when packages are updated). We can't expect that people will compile.

---

### Post by rykel on 2007-10-14
I am also interested in such a device!!

Well, PDAs, 12" laptops and 7" UMPCs are the closest you can get to this perfect Ubuntu handheld, but unfortunately their prices are still primetime.

Please keep us all informed if you do find someone who is selling this dream item and I hope they ship to Singapore too.   :popcorn:

---

### Post by jdq997 on 2007-10-14
EEE PC.  Supposed to be coming out in the next week.  Should run Ubuntu very nicely.  Not exactly what you are asking for, but the best option I can think of.  7 inch UMPC $200-300.

 - Jason

---

### Post by aimran on 2007-10-14
> **McLogic said:**
> 
[list]
[*] the board (with CPU/GPU/RAM/FLASH/Ethernet/etc) for $120
[*] a screen for $60
[*] lithium ion battery for $100 (2 x $50 flat 3.7v)
[*] 2 Gig SD cards are $15
[/list]


*Starts planning on how to put those all together*

---

### Post by odzk on 2007-10-16
wow probably what u want is a future phone/pda, just wait 5-10 years from now and you'll have what u want. ;)

---

### Post by leetrefz on 2007-10-23
[http://www.openmoko.com]("http://www.openmoko.com")

---

