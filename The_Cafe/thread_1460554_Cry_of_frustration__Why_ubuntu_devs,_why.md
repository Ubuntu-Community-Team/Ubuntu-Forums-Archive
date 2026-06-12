---
title: "Cry of frustration:  Why ubuntu devs, why?"
date: 2010-04-23
forum: The Cafe
---

### Post by LeifAndersen on 2010-04-23
I really love open source, but sometimes, it falls flat on it's face...this is one of those times.  I got a sony vaio vpc eb11ffm from best buy a few weeks back.  I brought a livecd, and put it into any of the machines I was considering buying, to see how well it would run.  It worked well in the vaio, except for one major flaw, the sound wasn't working.  (I found another one later after I bought it, the system wouldn't be stable if I had compiz on it).

Anyway, the thing even comes with a version of linux on the machine, for 'quick boot web surfing', and the sound works in it just fine.  Also, I even was able to find a fix for the sound.  It's not do to any lack of drivers, but one, just one configuration error that ubuntu makes when it's installing.  I go to report the bug, and I even provided the fix to go with it, and it was rapidly merged with another similar, but slightly different bug, and was pronounced to be fixed.  I upgraded to the RC that was created today, and nope the problem is still there.  And short of opening another bug report, with the same problem, I can't think of anything to do...grr...

Yes, I know canonical says not to run 10.04 on a machine you need to be stable, but I don't have much choice.  For some reason, 8.10 won't even boot onto the machine, and I don't want to go back to windows.

I know you people try hard, and I thank you for it.  But sometimes, I just have to rant in frustration, I want my sound to work out of the box.

Thank you for your time.  And I'm sorry if this is in the wrong spot.

---

### Post by macogw on 2010-04-23
Companies that make hardware do stupid things like not properly setting up the sound card's info in the BIOS, calling 2 different sound devices the same model numbers so that they can't be programatically distinguished, and making undocumented tweaks to hardware.  The only reason the hardware works in Windows is because they hack around it in the driver which they make specific to that hardware and preinstall for you (ie, if Windows just relied on the hardware being made to actually fit the specs, it wouldn't work there either).  If the hardware people haven't been kind enough to provide complete specs for that specific piece of hardware as integrated on that motherboard (because yes, same chip + different motherboard IS different)...and they almost never are... the only way it'll work is by reverse engineering it.  

So go file a bug.  ```
ubuntu-bug linux
``` It's much more likely to work than whinging here is.  Though of course it won't work for 10.04 at release time since that's only a week away and YEAH RIGHT at getting a kernel change before then.

---

### Post by Khakilang on 2010-04-23
Sorry to hear your frustration. Drivers is an issue with Linux because not all hardware come with Linux drivers. You have to download their source from their website and compile it yourself. That's what i gather. Lucid is just a week away so why not wait awhile and try it.

---

### Post by LeifAndersen on 2010-04-23
@macogw  Thanks for the information.  Also, I know it does more good than complaining about it here.  :)  As I tried to say, I'm moaning more about how the bug I filed got lost in gerontocracy more than I am about the issue itself (which is fairly trivial, although annoying, to fix).

@Koh Kook Loon, thanks.  Although, as I said, the drivers are there (and they work), it's just that they're misconfigured.

---

### Post by macogw on 2010-04-23
What configuration error is this? Are you giving a modprobe option in your /etc/modprobe.d/alsa-base.conf or something?  What was your bug report number?  Whoever marked it as a duplicate was Doing It Wrong.

---

### Post by LeifAndersen on 2010-04-23
Here is the bug now that's it been mushed with all of the other files. [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/525149](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/525149)  I also submitted all of the stuff that ubuntu-bug will submit.

Finally, here is a diff of the codec itself:

Diff for codec 0/0 (0x10ec0269):
---  
+++  
@@ -164,17 +164,17 @@
   Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
   Amp-Out vals: [0x80 0x80]
   Pincap 0x00003734: IN OUT Detect
     Vref caps: HIZ 50 GRD 80 100
   Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
     Conn = 1/8, Color = Black
     DefAssociation = 0xf, Sequence = 0x0
     Misc = NO_PRESENCE
-  Pin-ctls: 0x24: IN VREF_80
+  Pin-ctls: 0x20: IN VREF_HIZ
   Unsolicited: tag=0x00, enabled=0
   Connection: 2
      0x0c* 0x0d
 Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
   Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
   Amp-In vals: [0x00 0x00]
   Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
   Amp-Out vals: [0x80 0x80

---

### Post by cmat on 2010-04-23
8.10 didn't run at all on my new laptop. New versions of Ubuntu did work. Why not install 9.10 for the moment. If you have an new nVidia chipset it's hopeless on version of Ubuntu like 8.10.

---

### Post by iponeverything on 2010-04-23
Open another report on LP, reference the other report and explain to that the triage dude that merged it made a mistake.

They tend to go merge crazy on LP with the RC bugs as they try to knock as many out bugs as possible before the final, so there are a fair number of bugs that get misclassified. 

Worst comes to worst, you have the information and the fix in the wild. A few lucky people will find it and be to benefit from your frustration. I found lots of useful fixes digging through LP bug reports and treads.

---

### Post by ScarySquirrel on 2010-04-23
Hardware is an uphill battle for the entire linux community. 

[Ubuntu + Sound]("http://ubuntuforums.org/showthread.php?t=1460560")
Also, my signature is just another example of this. :( No one has responded to it yet, even to ask for clarification. in 2.5 years. Every linux kernel since that one still has that problem. 

Sound is no exception. Not Ubuntu's fault, but until someone makes a program that will automatically reverse engineer hardware and compile drivers for it, for many, Ubuntu will "just [not] work". Don't worry though. I'm working on it. Along with my adenovirus for boosting BMR. 

The increasing ubiquity of laptops will only exacerbate the lack of support by hardware manufacturers for linux. 

You should see me when I'm not cheerful.

---

### Post by LeifAndersen on 2010-04-23
@Cmat, woops, tired...I mean 9.10 didn't work, at all, but 10.04 did boot.

@ScarySquirrel, thanks.

---

### Post by ScarySquirrel on 2010-04-23
Thanks for what? Too tired for sarcasm, eh?

---

### Post by madjr on 2010-04-23
> **macogw said:**
> Companies that make hardware do stupid things like not properly setting up the sound card's info in the BIOS, calling 2 different sound devices the same model numbers so that they can't be programatically distinguished, and making undocumented tweaks to hardware.  The only reason the hardware works in Windows is because they hack around it in the driver which they make specific to that hardware and preinstall for you (ie, if Windows just relied on the hardware being made to actually fit the specs, it wouldn't work there either).  If the hardware people haven't been kind enough to provide complete specs for that specific piece of hardware as integrated on that motherboard (because yes, same chip + different motherboard IS different)...and they almost never are... the only way it'll work is by reverse engineering it.  

So go file a bug.  ```
ubuntu-bug linux
``` It's much more likely to work than whinging here is.  Though of course it won't work for 10.04 at release time since that's only a week away and YEAH RIGHT at getting a kernel change before then.

this is nice info

maybe ubuntu should get something similar going

> The only reason the hardware works in Windows is because they hack around it in the driver which they make specific to that hardware and preinstall for you

a community pool of fixes, all packaged up in deb files (like what you mentioned).

instead of just reporting the bug, users could also submit these quick downloadable fixes.

if the maintainers find it good/stable enough they could include it in upcomming releases.

would save effort on noobs having to go directly to the command line

---

