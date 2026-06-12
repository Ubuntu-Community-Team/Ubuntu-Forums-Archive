---
title: "ubuntu and Raspberry Pi"
date: 2013-06-13
forum: Ubuntu, Linux and OS Chat
---

### Post by squakie on 2013-06-13
I just don't know where else to ask this, so if it needs to be moved please do so.

I know Raspian on the Raspberry Pi is Debian based, and since Ubuntu is also Debian based, I was wondering if there is a version of Ubuntu that runs on the Raspberry Pi and it's architecture (Armtel  or some such thing).  I don't have a problem using Raspian, since the look and feel is pretty much the same, but wouldn't mind if I could just stick with Ubuntu all the way around.

As a side note, if you don't know what a Raspberry Pi is, you should research them on the net.  Very inexpensive, very small, and they make a nice little media center when XBMC is installed.

---

### Post by QIII on 2013-06-13
Last I heard, no.

Raspian is a pretty thoroughly reworked Debian.

---

### Post by Noah0504 on 2013-06-13
As far as I know, there still is no version of Ubuntu that will run on the Raspberry Pi.

Also, from the Raspberry Pi FAQ:
> Fedora, Debian and ArchLinux will be supported from the start. We hope to see support from other distros later. (Because of issues with newer releases of Ubuntu and the ARM processor we are using, Ubuntu can’t commit to support Raspberry Pi at the moment.) You will be able to download distro images from us as soon as the Raspberry Pi is released, and we will also be selling pre-loaded SD cards shortly after release.

If for some reason you don't want to run their Debian-based distro, they have a new "out of the box" software which allows you to choice from a few different distributions based on Fedora and Arch.

---

### Post by Bucky Ball on 2013-06-13
There's heaps of options. I have one running RaspBMC, which is basically XBMC for the Pi, and have it streaming vid/iview/radio from net and data from any of the four other computers in the house. Beautiful picture, sound, and RaspBMC is pretty rock solid. Nothing untoward at this point. 

You might want to look at Xbian. Apparently that is a bit of a blend of media centre/regular OS. Why not try something that is not a media centre? That is going to be reasonably 'Ubuntu-ish' (unless of course you use something non-Debian). I did read a website about someone getting Xubuntu up on a Pi, but don't know how that works. Anyway, good luck.

---

### Post by 1clue on 2013-06-14
Hope this isn't considered a hijack by anyone here, but since I have at least 2 enthusiasts paying attention I want to ask a question.

My parents are both almost blind.  I want them to get on the net so they can do email and watch videos that the rest of my family is sending.  They have a large screen TV which they can see fine, it's 1080p with HDMI.

I'd like to know how well this would work with two computer-illiterate 78-year-olds who can't seem to remember a lot?  I'm hoping for a simple menu-driven setup that they can use for email, photos and videos, both from a USB thumb drive and from YouTube or whatever.

Some sick, twisted part of me wants them on Facebook.  Most of the rest of my family is there, and it would give them a hook into our lives.

---

### Post by squakie on 2013-06-14
You may need to add a USB hub (AC powered - as the load may be too much for the power supply you might use with the Pi).  It has a web browser, so presumably you could do Facebook.  If they can handle desktop Ubuntu, then they could probably handle the Pi.  Keep in mind it is a relatively slow mono-processor of a different architecture, so don't be expecting all kinds of things.  It also isn't a full-blown version of Debian (nor the others, I suspect) - it's been modified to get it to run.

I have used mine to get on the net and research things for the Pi and XBMC.  I currently have one running raspian instead of the dedicated XBMC version.  So currently I have to start XBMC myself, but that's okay for now.  I'm trying to get this all set up for my sister and brother inlaw as a gift.  Currently using a wireless mouse and keyboard, and an USB 750gb hard disk.  I haven't done it yet as I'm waiting until I have everything set up and all the media (dvd's, pictures, cd's, etc.) actually loaded and working with XBMC, but....you can place everything but the essentials to boot on an external drive partition so that you only boot from the SD card.  This would also make things a little bit more responsive.

Since it will eventually need wireless connectivity, I have a powered USB hub to connect to it for the drive, wireless keyboard mouse, wireless networking adapter (my Tenda W332M [?] worked with no fuss), and room for more drives and USB flash drives if needed.  I plan to try having Samba running such that my sister and/or brother inlaw can use Handbrake on their Windows laptops and transfer the output to the Pi wirelessly so it is ready for XBMC.  I'm interested to see if/how big a performance hit for XBMC there is while Samba is running but not transferring anything and XBMC is playing back.

My biggest suggestion would be to check the net - there are forums for the Pi, youtube videos where you can see it in action, etc..

After I get this all set up for my sister and brother inlaw, I'm going to get some more of them as I just love the little dudes.  I'll rig one up as a XBMC unit using wireless to get movies from the other wireless Pi, so they can rsync and then move to the bedroom TV and continue watching the same movie right from where they left off.

I also just want to play with the dang things.  There's actually quite a bit there on the board and for $39 to $40 you can't beat it.  The GPIO pins are on the board, along with voltage and ground pins, etc., so you can interface to a lot of experiments, and I love to experiment.

Also working on adding wview to one so my niece's husband can hook up his Oregon Scientific weather station to it.

EDIT:  just remembered another possibility, slightly more money, but still under $100.  There is something called the PCDuino which has a version with a lot better processor and runnning Ubuntu.  There is no where around here in Minnesota that i've been able to find that even carries them.  Pi's on the other hand are quite well stocked and restocked at our local Micro Center - I assume other places carry them as well but I just go to Micro Center for most things - it's fun to look while buying ;)

---

### Post by Bucky Ball on 2013-06-14
*Thread moved to **General Help**.*

@ 1clue: Yes, I would consider it hijacking and would move my post and the last two posts to their own thread normally, but as squakie started the thread and happily replied to yours, what the hey. Probably avoid in future, though. ;)

Nicely put, squakie. You have done your research. The PCduino connects with the Arduino boards by the looks, another item you'd like if you haven't already got one or two:

[http://www.arduino.cc/](http://www.arduino.cc/)

There is also a camera board for the Pi (available at Element14 I think).

I think if you are looking to run a full blown Ubuntu, the Pi is not the place to go. It was never really intended for that and one of the only reasons it's come this far is the 1080p capabilities built right into the same chip. I don't know if you'd have any luck running anything like, say, Firefox. There are no plans I know of no plans for a more powerful one anytime soon. They were made as an educational device originally.

---

### Post by jfbooth on 2013-06-14
Here are friendly 2 cents.  I have a model B Pi running Raspbian Wheezy.  Have not had it very long.  I purchased it with a preloaded SD card 4GB, a usb WIFI dongle, a compact USB Keyboard w/ mouse USB port, a 4-port USB hub - USB powered which I do not use (yet).  It is connected to a 20" LG lcd display via HDMI.  Being preloaded, .. very easy to set up ... and seems to run impressively well.  I can't get sound out of the Display .. only out of the audio port with headphones ... but there is a fix for that ... I just have not found it.

From my time in forums etc it is apparent there are MANY distros being used on Pi ... but I only have limited experience with Raspbian.  I dumped the provided browsers for Chromium.  My setup does not seem to do (much) multimedia.  It came with a 'player' but it SEEMS that a lot of software needs to be installed b4 it will do anything.  Not sure ... but with this 'player', I have not got anything to work ... mp3, mp4, .wmv. ... nothing.  Have not had time to look further into this.  

It won't do a YOUTUBE video due to a FLASH issue .... and probably never will.  This is my greatest disappointment:

[http://blog.christosoft.de/2012/08/flash-on-the-raspberry-pi/](http://blog.christosoft.de/2012/08/flash-on-the-raspberry-pi/)

Is this a 'review of the Rasperry Pi"?  No, it is advice that I don't think it is suitable for Mr. Squakie's lovely parents.  Then again ... my acquaintance with mine is quite 'freshman' at this point.

---

### Post by Bucky Ball on 2013-06-14
Yes, there is a fix for that, but it's strange you have that problem as the audio is forced to HDMI by default on first boot. Hmm. Perhaps not with Raspian Wheezy, but RaspBMC is built on that I think. Updates from Wheezy repos. Anyway ...

You could try editing the /boot/config.txt file and adding:

```
hdmi_drive=2
```

... at the end of the file. From here:

[http://www.raspberrypi.org/phpBB3/viewtopic.php?t=5062](http://www.raspberrypi.org/phpBB3/viewtopic.php?t=5062)

That should force audio to HDMI and you are in for a big difference I imagine. Make sure you have your volume down before booting after the change.

---

### Post by 1clue on 2013-06-14
At some point I'm gonna have to get one, but I don't think my parents are going to be part of that.

IMO an operating system is best when it uses only a tiny part of the system resources, so I don't think I would put any *buntu on a pi.

I might look into that bigger PCDuino whatzit though, sounds interesting.

I find myself a bit disappointed at the pi guys though, I would have called the second edition a Pi r2, and the third 43 pi r3.  I love puns.

Sorry for the diversion, guys.

---

### Post by efflandt on 2013-06-14
What specifically about Ubuntu do you want the Raspberry Pi to do?  As it is, Raspbian is Debian based like Ubuntu, so if you are familiar with Ubuntu, it is easy to find your way around a Raspberry Pi. Since the Pi uses lxde it is similar to Lubuntu. Many applications that are not installed by default are available using apt-get, aptitude, or you can install synaptic. You don't really need Unity, you can just use desktop launchers.

It is not real quick with single core 700 MHz (or whatever you reliably overclock it to). But a nice thing about booting from SD card is that you can totally change its function by switching SD cards. You can have one with Raspbian for doing general thinks or playing around with programming. You can have another with one of several XBMC versions for multimedia (which has some internet TV stations, but will not do things like hulu or netflix). And when someone asked how to boot it into a terminal program, I figured out how to have one boot right into Quake3 (which runs quite good on the Pi). The autologin script I found required the korn shell, but it was simple enough to install ksh. It worked even powering the Pi from the USB port on an HDTV using HDMI for audio/video and using wireless keyboard and mouse (1 Logitech unifying receiver for both).

---

### Post by Bucky Ball on 2013-06-14
@ efflandt: Sounds good, but I wouldn't advise powering the Pi from USB for any lengthy period, especially while running peripherals. If the Pi's performance starts getting flakey, immediately desist. 5V, 1A PSU best with powered USB hub. PSU cheapest in town, about AU$6 from Element14. Love the Pi.

---

### Post by squakie on 2013-06-15
I love the little arduino's too.  Lot of fun for experimenting.   After I get caught up with all the dvd, etc., loading for the media center I can get back to my next arduino project: using the heat detector sensor (well, a little more than that) to trigger a timer when my cat enters his litter box, counting down a couple of minutes, then running an actuator that sprays air freshener from a can (yep - I think of some odd things :-)  ).

---

### Post by Bucky Ball on 2013-06-16
> **squakie said:**
> ... trigger a timer when my cat enters his litter box, counting down a couple of minutes, then running an actuator that sprays air freshener from a can (yep - I think of some odd things :-)  ).

Little off topic but ... 

If you haven't seen it, try:

*Making Things Talk*, Tom Igoe.

A few years old but for Arduino. There's probably a revised edition by now. *Physical Computing* (O'sullivan, Igoe), is another.

Just thought I'd share and then butt out, carry on. ;)

---

### Post by squakie on 2013-06-17
Please continue - I don't mind this being about all things micro - not just he Pi's.! I don't know if there is, but perhaps a sub-forum for users of these devices (yeah - I know it would have to be a non-Ubuntu thing) would be a great place here.  Sharing ideas on uses/interfacing with Ubuntu (things like netowkr, XBMC, etc.) could be quite interesting.  I know those forums already exist else where, but one here could be fun as well.

It's too bad that it's extermely difficult to find one of the old (and I'm talking OLD) WD disk controller chips around anymore.  I wrote a driver for both floppy and hard disks for one of those in what seems eons ago now - don't know if I could even think it out now (I've gotten old and mind has gotten lazy - or maybe I've gotten lazy?? ;) ).  It might be fun trying to interface one to the Arduino (unless of course someone already has).

---

### Post by squakie on 2013-06-17
O, just remembered - I was thinking there was a version of the PCduino that was actually running Ubuntu from flash - that's the main reason I mentioned it since if someone was more comfortable with ubuntu itself there is still an option that way.

Can 't find one anywhere around here, so I can't pick one up and play with it and then make a little more educated comment on it.  I wish I could find one around here somewhere (Minnesota in the U.S.).

---

### Post by squakie on 2013-06-17
> **jfbooth said:**
> Here are friendly 2 cents.  I have a model B Pi running Raspbian Wheezy.  Have not had it very long.  I purchased it with a preloaded SD card 4GB, a usb WIFI dongle, a compact USB Keyboard w/ mouse USB port, a 4-port USB hub - USB powered which I do not use (yet).....

Forgot to reply to this part for you.  Keep in mind that the max any given USB port can support is 500 milliamps.  Therefore, each USB device could theoretically draw 500 milliamps each.  So let's take your 4-port hub:  4x500 millamps.  This will well exceed the current limit of the single USB port you have the hub plugged into.  In addition, I suspect most people are going to powering these off of something similar to a cell phone charger as long as it's the correct voltage.  Most of these don't take more than perhaps a 700 milliamp load in totla.  So, you want to power your PI, it's 2 USB ports (remember up to 500 milliamps each) and all the devices on your hub  off 1 little power supply?  Can you say something will toast eventually?  It would be highly recommended to get an A/C powered hub and connect all your USB devices to it, and plug the hub ONLY into the PI - nothing in the other UISB port.  The current draw will eventually just be too high for either the power supply, the Pi, or most probably, both.

So, to take the semi-technical out of it, ALWAYS use an A/C powered USB hub and plug all your USB devices into it, and the hub as the ONLY USB device plugged directly into the Pi.

Also keep in mind that if you like to play like some of us, you need to understand power load, programmable IO, etc..  Without some understanding of that, be sure to follow a tutorial or book for circuits and fun with the GPIO pins, etc., on the Pi.

Again, to me anyway, these little dudes are a trip.  They take me back 40 years to the start of what was my career right out of college.

---

### Post by Bucky Ball on 2013-06-18
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Probably better here at this point.

---

### Post by squakie on 2013-06-18
Thanks Bucky Ball.  I'm going to take a look at the resources you posted for the Arduino when I finish up this project with videos, XMBC, etc.. ;)

---

### Post by Richard_Butler on 2014-06-05
Have You tried DSL (damn small linux) on the Raspberry Pi ?  Just a passing thought,  I was thinging of getting a Pi to play with.

---

### Post by 3rdalbum on 2014-06-06
> **Richard_Butler said:**
> Have You tried DSL (damn small linux) on the Raspberry Pi ?  Just a passing thought,  I was thinging of getting a Pi to play with.

No, DSL is only available for x86 and the Raspberry Pi has an ARM CPU.

---

### Post by Bucky Ball on 2014-06-06
Way out of date. Please start a new thread. Necromancy. 

***Thread closed.***

---

