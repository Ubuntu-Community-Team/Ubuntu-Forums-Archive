---
title: "Thank you Ubuntu and the open source community"
date: 2015-06-07
forum: The Cafe
---

### Post by kurt18947 on 2015-06-07
[RANT]
 I have once again come to appreciate the usability of Ubuntu and its kin. I had an R61 Thinkpad listed for sale on a local want-ads site. I got a legitimate inquiry, prospective purchaser lived nearby so began to restore it to factory default. It came with Windows Vista and I had the factory restore disks so no problem, right? HAH!

 
 
 I started out running DBAN (couldn't get HDPARM to work for some reason). I started feeding is CDs and all was proceeding apace. About 50 minutes into the process, I got a &#8220;bootmgr.exe not found&#8221; message. Huh? A google search found one cause was the hard drive not being listed as the first boot device. I'd changed the boot order to make USB devices first. I'd restored the BIOS to default but no problem, made the HD the first boot device and started the process again. That error message went away but another took its place. I googled and tried a few different things, taking about 1 hour per try. No luck. 

 
 
 I finally threw my hands up, called the prospective purchaser. I explained the situation and offered to either install Win7 in demo mode that would expire in 30 days or install XP. In talking to him I was pretty sure installing a linux distro would not work. I explained about XP being out of support but he said go ahead. XP installed with no issues though I'd forgotten where most of the controls were found so that took a while. I'd also forgotten the joy of having virtually NO drivers installed by default. Lenovo has a tool that when run a few times will install the proper drivers. In order for this to work, I needed a network connection. Off to Lenovo's web site. I found several ethernet and wifi drivers for that model. None of them worked. I finally downloaded the windows driver for a Trendnet USB wifi device and was then able to run the Lenovo update tool.

 
 
 Most of the drivers installed properly, except the WiFI. I knew from lspci that it was an Intel 3945 so off to Intel's site to download there. Intel's site told me that driver had moved but seemed to have left no forwarding address. I then tried download.com but that insisted I download a bunch of other crap too. I finally did find a source that seemed clean. Installed that and most things worked. Fingerprint reader & smbus driver didn't but I was tired of messing with it. Guy came, tried it, paid and left. I had started at 6 a.m. (0600) and the thing left the house at 6:30 p.m. (1830) I sold the machine for $40, the display was getting dim and ethernet port was occasionally flaky. I wonder how much I made per hour?

 [/RANT]
 
 Thanks, I feel better.:) This machine had numerous linux flavors installed and none took longer than about 20 minutes to get to the same state.

---

### Post by Mike_Walsh on 2015-06-07
Makes you wonder why people struggle on with Windows..! Waving bye-bye to it last year was the best move I ever made (seriously). Linux rules, as far as I'm concerned; my boxes now do everything I want a computer to do (and then some)...and I can configure them to behave exactly the way that **I** want them to.


Regards,

Mike. :)

---

### Post by kurt18947 on 2015-06-08
Mike, I agree but then yesterday I was reminded why it's a good idea to keep a Windows install functioning. I bought a factory refurbished Logitech keyboard that uses their unifying receiver.  It came without a receiver but no worries, I had 2 already. Checked the batteries in the keyboard, turned it on and -- nothing. I tried various iterations of unplug and and replug the receiver, turn the keyboard power off and on, still nothing. I then remembered software on Logitech's site to assist with pairing receivers and devices. Fired up Windows 7, (of COURSE it's only available for Windows) downloaded the app, fired it up and both keyboard and trackball paired up as advertised. Once paired both worked as expected with Ubuntu.  And to be fair, installing Win 7 and Win 10 preview are pretty painless.  Well, except for the fact that Windows 10 preview installed fine then cratered unrepairably when I tried to activate a wireless connection:lolflag:. Oh well, reinstalls are not unusual when using developmental OSs as we linux users know.

---

### Post by Mike_Walsh on 2015-06-08
Oh yes; I know what you mean. I have a ZoneTouch T400 mouse (with the Unifying receiver), and a keyboard.....but mine is the K120 (which is a wired one). Luckily, the T400 got left in the correct configuration when I quit XP least year. I can't help feeling, though, that the Logitech software is incredibly bloated for what it does (80 MB+, from what I recall); the only thing it does that you can't adjust under Linux, is the number of lines that you 'jump' while scrolling. The 'sideways' scrolling on the 'touch-strip' works OOTB in Ubuntu... 


Regards,

                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        Mike.

---

### Post by Welly Wu on 2015-06-08
I have multiple Logitech products and I almost always use USB 2.0 wired connections because I know it will work regardless of which PC I am currently using. The only exception is the Logitech wireless touchpad (old model) that came with the Logitech Unifying Receiver. I plugged it into my ZaReason Zeto desktop PC and my Lenovo IdeaPad Y510P and it works. Now, some of the specific Microsoft Windows 7 gestures don't work with GNU/Linux, but the basic features do work right out of the box.

I had enough of Microsoft products and services when I got Windows 8.1 64 bit. It crashed on me ten times in less than one year. Most of it is my fault, but it was notoriously worse than Vista. It's a bear to install and it's like pulling teeth to get it up and running smoothly.

GNU/Linux is the superior desktop and mobile operating system that the world has embraced. Google Android is not pure Linux, but it is the most popular mobile operating system that uses older Linux kernel versions. The latest Ubuntu 64 bit LTS GNU/Linux desktop operating system is my choice out of all of the other UNIX like distributions because it just works right out of the box 99.9% of the time. Installing Ubuntu takes less than 10 minutes using modern PC hardware and especially with SATA-III 6 GB/s solid state disks. I don't need to worry about specific device drivers again. It's simply plug and play the way that Microsoft Corporation failed to make it out. No device driver installation is required for each device on each type of connector. Ubuntu in particular just gets out of my way and it respects my intelligence and privacy too. I don't need to have a big question mark in the back of my mind about what data leakage issues are going on behind my screen when using GNU/Linux.

Since I'm retired now for several years, I no longer need access to high end proprietary software applications. What I already paid for is sufficient for my daily needs. I'm seeing more hardware manufacturers and software vendors are porting their wares to GNU/Linux slowly and gradually. There are more commercial GNU/Linux software products available for purchase that have been successfully ported over. I'm not missing Microsoft any longer.

---

### Post by Mike_Walsh on 2015-06-11
Just out of sheer curiosity, I attempted to run my old Logitech 'SetPoint.exe' setup utility under Wine. The initial 'Start' screen came up (albeit very slowly) and then...it simply froze solid.

Worth a try, purely as an experiment, but really, the results were about what I would have expected... :p


Regards,

Mike.

---

