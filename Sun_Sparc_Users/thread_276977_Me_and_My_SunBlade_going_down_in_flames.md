---
title: "Me and My SunBlade: going down in flames"
date: 2006-10-13
forum: Sun Sparc Users
---

### Post by cptnapalm on 2006-10-13
So my Sun Blade got here and so my adventure began...

In addition to the SB 2000, I also got a Sun USB keyboard and mouse as well as a Sun to VGA converter.  The only non-Sun thing was the monitor.  This has lead to hours of fun.

Last Night:  I plug the USB keyboard and mouse in, connect the Sun to VGA cable to the SB and to the monitor and turn it on.  The power LED blinks then goes solid green.  The fans, which started very loud, become rather quiet.  But there is no video output of any sort.

I go through this with a few old monitors.  One of them, a ViewSonic 4E does display some output, but it is quite garbled.  I am able to read, albeit barely, "Probing for System Devices" or something very close to that.

So I figure that I'm getting someplace.  The keyboard LEDs do not flash during boot, but they the keyboard does respond properly to the Cap Lock and NumLock keys, so it does appear to be working.

What this means, according to the service manual, is that it was off, then booting then all internal subsystems were in lowest power consumption mode then, finally, at least one subsystem at full power and the self test completed successfully.

So.

I booted it up again, having read found some advice (most of which was quite foriegn to me) and gave it a shot.  What I was supposed to do, so I understood, was to stop the boot sequence and then change the default resolution of the Sun Blade to that of a 1024x768@60Hz.  So I hit Stop A.  And the fans go wild.

The fans in the case, that is.  From near silent, they became as noisy as they were when the machine was first turned on.  And they don't shut up.  I type in the stuff I have read.  No idea what actually happened.  After a few more minutes of noisy fans, i tap the power button.  Then after a bit, it shut down.

Today:

Got an antique P133 out of the closet because it has a serial port.  My laptop does not.  Windows 2K is on there.  Really.  I find a serial modem cable with a DB25 male and DB9 female connectors.  Following another guide, I boot up W2K to use hyperterminal.  Set the baud rate and all that stuff accordingly  unplug the keyboard, mouse and monitor from the Blade then boot the Sun.

It gets noisy with the fans and they don't turn quiet.  There is no output on HyperTerminal.  Try a few options but still nothing.
Power down the Sun Blade and restart it after hooking up the keyboard, mouse and semi-functional monitor.

This time there is no garbled output.  The Sun *is* sending something because the monitor displays... various tones of changing black when I later shut it down again.  The keyboard does not respond to Caps Lock nor to NumLock.

I'm kind of at a loss.

---

### Post by netztier on 2006-10-14
> **cptnapalm said:**
> So my Sun Blade got here and so my adventure began...
Last Night:  I plug the USB keyboard and mouse in, connect the Sun to VGA cable to the SB and to the monitor and turn it on.  The power LED blinks then goes solid green.  The fans, which started very loud, become rather quiet.  But there is no video output of any sort.

I can only talk about the experience I have from listenting to the Sun Blade 1000 booting at my work place. What you describe sounds quite normal. While the Box is at the OBP prompt (i.e. what you would call "the BIOS" in a PC), the fans run at full speed at unbearable noise. Somewhen while booting the OS's kernel, some kind of temperature control kicks in and throttles the fans.


> **cptnapalm said:**
> 
This time there is no garbled output.  The Sun *is* sending something because the monitor displays... various tones of changing black when I later shut it down again.  The keyboard does not respond to Caps Lock nor to NumLock.


Are you positive that the serial cable actually **is** a null modem? The serial port parameters should be 8N1 (8 bits, no parity, 1 stop bit), 9600bps and neither Hardware (aka RTS/CTS) nor software (aka Xon/Xoff) flowcontrol.

You might even try ripping out the Video card and leaving the Keyboard and Mouse unconnected - if the Sun is okay, it definitely should give some output on the console port. To bring the machine to the OBP prompt, you need to send a "break" signal from the terminal emulator (Hyper Terminal, VanDyke CRT, whatever...). AFAICR in Hyperterm, you can send the break signal by pressing Ctrl+Break,this should bring you to the "ok> " prompt if the OBP.

regards

Marc

---

### Post by cptnapalm on 2006-10-14
The cable I used was something I have had forever.  I figured I would give it a shot.  It has the 25 pin male and 9 pin female connectors.  My best guess is that it was a modem cable.  I am going to try to find a guaranteed null modem cable tomorrow.

The inital boots (despite the lack of useful visual information) seemed to be fine.  As the fans had kicked down to near silent levels, I presumed that it was behaving as it should.  After the Stop stuff, the fans never shut up.

In the manual (the huge 342 page one) it said that with a min setting (can't remember what right now, I'm at work) it would be 3 to 4 minutes to get through, but with it on max, it could be upwards of 40 minutes.  Tomorrow morning, I intend to turn the thing on and go to the store to get a null modem cable.  If it is quiet when I return, then I'll assume I had somehow set it to max the other day.

As far as the HyperTerminal settings, I've seen instructions which run the whole list as far as flowcontrol.  I'll make sure to have it set to Xon/Xoff.

This little adventure reminds me of putting PCs together years and years ago.  Everything has its mystery to be solved.  While it can be head bashingly aggravating, it is still kinda fun :)

EDIT: I'm pretty sure that the cable I have is a modem cable.  So, I really need a null modem adapter which will switch the proper pins on one side or the other.

---

### Post by cptnapalm on 2006-10-16
A brief follow up.

Indeed the cable was not a null modem cable.  A null modem adapter solved that problem.

And we have ttya output!

My current problem is that the alias disk1 has two entries in devalias.  The one that the machine insists on using does not work.  The one that it won't use does work.  I'm back to getting garbled video output, but it is red instead of green now.  Even though I set it to do 1024x768x60, a monitor which I know does that won't show anything.  The ViewSonic does still show output, but I don't think that it does it at that resolution.  Its too late tonight to deal with it.  How do you set a hostname under Solaris anyway and why does it not do that when doing all the base setup stuff?

I'd like to get an LCD for this thing, but I've read some odd things about using PC LCDs with Sun systems.  If it is a TFT, should it work?  I'd go with Sun, but they seem to be excessively expensive and not as good.

Any thoughts or comments are appreciated.

---

### Post by netztier on 2006-10-16
> **cptnapalm said:**
> 
My current problem is that the alias disk1 has two entries in devalias.  The one that the machine insists on using does not work. The one that it won't use does work. 

Uh, can't help you there, this is going deeper into the inner workings of OBP than I can keep up with.

> **cptnapalm said:**
> 
I'm back to getting garbled video output, but it is red instead of green now.  Even though I set it to do 1024x768x60, a monitor which I know does that won't show anything.  The ViewSonic does still show output, but I don't think that it does it at that resolution.  


Sounds like swapped RGB Signals or broken wires in the cable to me. Do you know what kind of video card you have there in that box? You were talking about a VGA adapter - so I assume it has a 13W3 outlet. With a working adapter and a good VGA cable, this should be no problem. Does your Monitor have a 5x BNC (H.Sync, V.Sync, Red, Green, Blue) instead of a D-Sub-15 input, and some of them might be swapped?

In OBP, did you use the "setenv output-device screen:r1024x768x60" command? (can't remember the exact syntax)? Or did you set the screen resolution by some other means?

> **cptnapalm said:**
> 
I'd like to get an LCD for this thing, but I've read some odd things about using PC LCDs with Sun systems.  If it is a TFT, should it work?  I'd go with Sun, but they seem to be excessively expensive and not as good.


My experience is different: I've been using half a dozen of Ultra 2 (Creator UPA), an Ultra 5 (ATI, onboard) and a handful of Ultra 60s (Creator 3D) with three different TFT LCD Screens (NEC, Video7, EIZO) at home and never had a problem with getting screen-output. At work, we used to have dozens of Sun Blades with Creator 3D all over the place with EIZO LCDs of at least four model generations without any problems.

best regards

Marc

---

### Post by cptnapalm on 2006-10-16
I'm still not sure whether it is an Elite or a Creator card.  I did try to get the side panel off but none of the screwdrivers I tried quite fit and I didn't want to strip the screw.

I did to the exact setenv output-device that you posted.  It comes up when I do a printenv output-device.  The monitor, while old as hell, does do it under Ubuntu.

There is something I read today about csync, which I don't quite get, but that apparently is a problem other people have had.

Much thanks for relating experiences with TFT LCDs.  I'm pleased to know that a non-Sun TFT should work fine.  Once I get in a position to do so, I'm going to find out what resolutions that the card supports then get a matching TFT LCD.

Hopefully, once I get the video output sorted out and find how to delete the excess devalias, the sailing will be smoother.

At a minimum, it has been a learning experience.

---

### Post by netztier on 2006-10-17
> **cptnapalm said:**
> There is something I read today about csync, which I don't quite get, but that apparently is a problem other people have had.

Sounds like "sync-on-green" to me. Search on [Google]("http://www.google.ch/search?hl=en&q=sync-on-green&meta=") brings up things like this ...

[VGA to Sync-On-Green adapter ]("http://www.raphnet.net/electronique/sync-on-green/sync-on-green_en.php")

... which at least might explain what is going on. Maybe there's even a register bit (or something along that line, maybe even a jumper to set?) on the graphics card you could configure so it'll bring up separate h.sync and v.sync signals instead of pulsing in on the green color signal?

At least for some of Sun's video cards, this seems possible, see also **docs.sun.com** search for [*sync-on-green*]("http://docs.sun.com/app/docs?q=sync-on-green")


**[COLOR="Red"]Update:[/COLOR]**
Browsing through [sonnenblen.de]("http://www.sonnenblen.de/") (german Sun hardware oriented forum), I found a [thread]("http://www.sonnenblen.de/index.php/topic,3763.msg20961.html#msg20961") (see last posts in thread) about warning the users about 13W3<->VGA adapters that were for SGI (and did conversion to sync-on-green), not for SUN (which provides sync-on-composite), if I understood correctly.

So you might want to check if you have the right 13W3<->VGA converter for a Sun Box.


regards

Marc

---

### Post by cptnapalm on 2006-10-17
I'm now 90% sure that the card is a Creator 3D series 2 (or 3 maybe...) with 13w3 output.

The 13w3 to vga cable I have has the Sun logo on it, but I haven't seen one like this on my searches.  Mostly, I have seen small adapters and adapter cables which are about two feet long.  This one is only one foot long.  I've looked for a part number, but I can't find one.

I do believe that the adapter cable is at fault.  I've hooked up a more modern monitor (HP v17) and it would wake up on boot, but display nothing.  It tried to get the resolution, but when I used the command line to find the supported resolutions of the monitor, it said that it could not find the EDID information, so would assume a 19" Sun montior.

Oddly, if I set the framebuffer to svga, the output goes to ttya.

---

### Post by netztier on 2006-10-18
> **cptnapalm said:**
> It tried to get the resolution, but when I used the command line to find the supported resolutions of the monitor, it said that it could not find the EDID information, so would assume a 19" Sun montior.

These are run with 1152x900 at some 76Hz, if I remember correctly. Can the monitor you hooked up to it handle this?

> **cptnapalm said:**
> 
Oddly, if I set the framebuffer to svga, the output goes to ttya.


Is that in Linux or in Solaris? And what/which output goes to ttya? The X11 output? not really, is it? (?)

regards

Marc

---

### Post by cptnapalm on 2006-10-18
The console output said that it couldn't find the EDID so the Sun Blade would assume a Sun 19".  That was annoying as I had just resolution to 640x480.

The svga thing was in OBP  (I should have been clearer on that and other things probably).  Once Solaris started up, I got the stuff about starting X.  Oddly enough, once that happened, the monitor, which had been awake although displaying nothing, immediately went to sleep.

When I started up the machine after changing to svga, even though there was a monitor attached, I got the output on the HyperTerminal.  Once I gave a specific resolution to use, then it would attempt (and fail) to display on the monitor.  Strangely, I was using the keyboard attached to the Sun, but reading output on the terminal.

While intermitently typing this, I came across a posting about an Elite 3d: [http://forum.sun.com/jive/thread.jspa?forumID=246&threadID=67177](http://forum.sun.com/jive/thread.jspa?forumID=246&threadID=67177)  It is the second post which caught my eye.

<quote>It could be that you have an old out-of-date adapter that doesn't connect the vsync line (or the EDID lines either)</quote>

The above recalls that when probing for the monitor, the Solaris couldn't find the EDID even though I'm pretty sure that a 2 year old HP monitor would respond if queried properly.

Newly found link on Sun Framebuffers: [http://www.sun.com/products-n-solutions/hardware/docs/pdf/806-6054-10.pdf](http://www.sun.com/products-n-solutions/hardware/docs/pdf/806-6054-10.pdf)

This other set of postings ( [http://www.webservertalk.com/archive103-2006-2-1381453.html](http://www.webservertalk.com/archive103-2006-2-1381453.html) )mentions the sync-on-green, but states that the Creator 3d does not support it.  Mention is made here too of needing something which supports csync and that not all adapters are made equal.

I've searched so much on this issue, I've even bumped into postings ( [http://playstation2-linux.com/sog.php](http://playstation2-linux.com/sog.php) ) on linux for PS2 with its sync on green issues.  The reports there of both constantly rolling, garbled output is like my ViewSync while the black screen is like all my other monitors. 

From what I've read, the convertor should have a part number molded onto it.  That it does not and is a full foot shorter than other Sun made cables leads me to think that the convertor may have been modified at some point.  I'm wondering if perhaps this cable was modded so as to hook it up to an SGI monitor or perhaps it worked just fine with a Sun monitor thought it doesn't with a PC one.

Ack.  :)

---

### Post by ubumatic on 2006-10-27
Hello,

I have done my share of fighting with Sun video cards. I have now a working configuration.

First of all, Creator3D doesn't use Sync on Green, but rather composite sync:
[http://72.14.221.104/search?q=cache:-OMQiFwsT9UJ:sunsite.ualberta.ca/Sun_Resources/Just_The_Facts/Expert3D-JTF.ps+elite3d+composite+sync&hl=fi&gl=fi&ct=clnk&cd=6&client=firefox](http://72.14.221.104/search?q=cache:-OMQiFwsT9UJ:sunsite.ualberta.ca/Sun_Resources/Just_The_Facts/Expert3D-JTF.ps+elite3d+composite+sync&hl=fi&gl=fi&ct=clnk&cd=6&client=firefox)

I have an Elite3D but some of this may apply to Creator3D.

Originally I had a no-name 13w3 which was clearly defective, it worked only when Solaris started X/gdm, which made using OBP impossible. Buying an original Sun adapter helped a bit but my Samsung CRT woke up so late to Elite3D signal that Solaris boot was well underway.

The display I'm using now is Samsung SyncMaster 204B. It does separate sync, composite sync and sync on green. It wakes up to Elite3D signal early, you will actually get to see the sun and CPU/memory/OBP text and ok-prompt before the OS boots...how cool is that?

You may need to do some magic to get X running. Elite3D requires that a certain firmware binary (afb.ucode) is loaded to the card during boot. I grabbed the afb.ucode from Solaris patches and installed debian afbinit ('sudo afbinit /dev/fb0 afb.ucode' does the magic). In addition, make sure you choose the right display driver for X. For Elite3D it is sunffb.

And yes, the fans are blowing. Hopefully I will get Edgy running, because I have this impression that bbc_i2c driver has been fixed in newer kernels.

---

