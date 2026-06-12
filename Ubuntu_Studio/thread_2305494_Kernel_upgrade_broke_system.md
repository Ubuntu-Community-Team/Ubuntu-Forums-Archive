---
title: "Kernel upgrade broke system"
date: 2015-12-06
forum: Ubuntu Studio
---

### Post by rlovi on 2015-12-06
I'm running 14.04.2 LTS, 64 bit Ubuntu Studio on an AMD Phenom x4 machine. I did an upgrade to low latency kernel 3.16.0.55.46 and all heck broke loose. The system would randomly freeze... sometimes the keyboard would stop working, then the mouse and finally the window environment would freeze. I thought it might be a video card issue so I removed the 750ti and ran on the onboard video card. Seemed to be more stable but then while I was away from the screen, the system fell back to a frozen console with errors and such and the one message that caught my eye was something about the cpu's being out of sync. 

I immediately thought it might be a kernel issue. Funny thing is I never had a kernel upgrade go bad since I've been using Linux since 1995. The system remained stable enough after a reboot to allow me to reinstall low latency kernel 3.16.0.52 (I removed the older kernel after the installation of the new one). The system has been running fine ever since. 

Anyone else have similar issues? If someone can point me to the log file that had the console errors it would be appreciated. I looked in var/log/ but so far haven't found it.

---

### Post by CrocoDuck on 2015-12-06
I would contact the[ kernel maintainers]("https://launchpad.net/ubuntu/+source/linux-meta-lowlatency/+bugs"), maybe by filing a bug report. I guess they will be interested in a issue causing such major problems.

---

### Post by rlovi on 2015-12-06
I agree though now it doesn't appear to be software related. 

I booted the wrong kernel by mistake this afternoon after the machine was off for a few hours and the system immediately locked up at the login screen. I rebooted with the older kernel and the system behaved in the same strange ways as before. Sometimes it would boot to the login screen but lockup at the desktop, sometimes it would never make it to the login screen before freezing and sometimes it would not even make it to the post screen. 

So I removed the 750ti video card once again and got into the bios setup using the onboard video card. I took a look at the power supply voltages and they were all correct and stable. Then the darn thing froze at the bios screen. So I took out two, 2GB ram boards and checked the remaining two which passed the memory test. And then the machine booted fine with just 4GB of ram and has been running an artificial life sim for three hours straight with no issues. But this is how it behaved after I switched kernels. 

Oh well, I'll figure this thing out sooner or later.

---

### Post by Bucky Ball on 2015-12-06
If it crashed in the BIOS it has nothing to do with Ubuntu but, as I think you've now discovered, is probably a hardware issue. 

Just a tip: Please use paragraphs. Blocks of text (affectionately known as 'wall of text') posts much larger than what you've posted will have the result of putting off potential helpers which doesn't help you at all. :)

Would help your cause to edit your two posts into a least a couple of paragraphs each. Good luck.

---

### Post by rlovi on 2015-12-07
> **Bucky Ball said:**
> 
Just a tip: Please use paragraphs. Blocks of text (affectionately known as 'wall of text') posts much larger than what you've posted will have the result of putting off potential helpers which doesn't help you at all. :)

Thanks, advice taken. :)

---

### Post by furtom on 2015-12-07
> **rlovi said:**
> I immediately thought it might be a kernel issue. Funny thing is I never had a kernel upgrade go bad since I've been using Linux since 1995. The system remained stable enough after a reboot to allow me to reinstall low latency kernel 3.16.0.52 (I removed the older kernel after the installation of the new one). The system has been running fine ever since.

You solved your issue, so this is just for conversation.

I've been running Linux almost as long, and I find the statement, "I never had a kernel upgrade go bad since I've been using Linux since 1995" incredulous, to say the least!

You are either the luckiest guy alive or this may be a tad of an exaggeration. 

Basically, in those days, we had to recompile for every upgrade -- modules at least, if not the whole kernel. Different distributions had different versions of gcc installed, etc. It was pretty much a many-hour project to update a kernel, more than not. Usually, one had to wait days or weeks for a hardware vendor like nVidia to catch up, or find a workaround, etc.

You must know what I'm talking about! Perhaps you and I have different concepts about what it means to "go bad."

These kids with Ubuntu today don't know how good they have it. ;)

---

### Post by rlovi on 2015-12-07
Yes, I know what you're talking about. :) If I remember correctly, usually stock kernels worked for me (a 386DX being the first computer I owned to run Linux). I do recall the multiple choice menus for compiling kernel options.

I don't recall being as frustrated as I am now having to deal with an intermittent problem that at first seemed software/kernel related. Though there's a remote chance it still might be, it appears now to be hardware related as the computer froze while I was exploring options in the BIOS setup. 

The computer seems stable now with two modules of ram removed leaving the first two slots filled. I'll see how long it holds up.

---

### Post by Bucky Ball on 2015-12-07
So that is sounding like two RAM slots are dead. Not unheard of. First and third or first and second or something else? Have you taken out the two sticks you have in there and replaced them with the other two to confirm it is the slots and not the RAM sticks (if they came in a pair they could be dead together)?

Do you consider this thread solved, or at least resolved? If so, please mark it that way (see first link in my signature). Doing so will not close this thread to further discussion. :)

---

### Post by rlovi on 2015-12-07
On this motherboard, Gateway DX4300, the first two slots are blue colored and the second two are yellow. I removed the third and fourth assuming the paired slots are not staggered.

No, I haven't switched ram pairs to see if it might be the ram or slots that are bad. I'm waiting to see if I can get a few days of stability first.

No, I don't think the problem is solved. I'll keep you informed of my progress.

---

### Post by Bucky Ball on 2015-12-07
Ok. Let's forge ahead. :)

Wait to hear how things are going in 48-72 hours then. Pretty sure you would see a problem well before that if there was one, but you never know. If all good, swap them to the other slots and see if that works or chuck the other two in the slots you know work and see how that goes.

I will add here that if these are new sticks they can sometimes need to be reseated once or even twice (or thrice). Another trick, and this sounds odd, is that sometimes the contacts on the new stick has some manufacturing matter on and doesn't contact properly. This is the odd bit: a quick rub of the contacts with a regular pencil eraser usually does the trick. Nothing vigorous.

---

### Post by furtom on 2015-12-07
> **rlovi said:**
> I don't recall being as frustrated as I am now having to deal with an intermittent problem that at first seemed software/kernel related. Though there's a remote chance it still might be, it appears now to be hardware related as the computer froze while I was exploring options in the BIOS setup. 

I've been there. we get so used to these quirks being introduced and then solved, that hardware as the cause is often the last thing to imagine, though it shouldn't be. :D

---

### Post by rlovi on 2015-12-08
> **Bucky Ball said:**
> 

Wait to hear how things are going in 48-72 hours then. Pretty sure you would see a problem well before that if there was one, but you never know. If all good, swap them to the other slots and see if that works or chuck the other two in the slots you know work and see how that goes.

Last night I cleaned the contacts of the ram I removed from slots three and four and then replaced the ram in slots one and two with them. I then ran the memory test and all checked out ok with no errors. So I cleaned the original two ram modules and placed them in slots three and four and ran the memory test again with all four modules installed. Still no errors. I ran an artificial life simulation all night and this morning the machine was still up and running. This is with the older kernel btw.

So I'm stumped. It looks as if the ram and memory slots are ok. Maybe the cleaning of the contacts and re-seating of the ram did the trick. Who knows. I'm reluctant to try the latest kernel again though that would be the next test. 

Is it possible for a kernel to mess a system up so bad as to require a computer to be shutdown and unplugged from the power source to reset everything? 

Dazed and confused.

---

### Post by Bucky Ball on 2015-12-08
> **rlovi said:**
> So I'm stumped. It looks as if the ram and memory slots are ok. Maybe the cleaning of the contacts and re-seating of the ram did the trick. Who knows.

It wouldn't be the first time this procedure has corrected things.

> **rlovi said:**
> Is it possible for a kernel to mess a system up so bad as to require a computer to be shutdown and unplugged from the power source to reset everything?

Guess that's possible. That certainly seemed to be the case with Windows! I haven't found that to be such an issue with Ubuntu, certainly not because of a kernel messing things up. Not sure how that would happen. User tweaking with a kernel or an app could screw things up, but booting to a functional kernel then the kernel gets nefarious and messes with things for no particular reason I can't imagine. Generally, a kernel either runs, with or without problems, or it doesn't. 

Still, first time for everything. Give the other kernel a shot. Can't hurt. If it won't boot, just reboot by hitting control+alt+F1 then type 

```
sudo reboot -h now
```

Before doing this do an update in the older kernel then reboot to the new one.

---

### Post by rlovi on 2015-12-08
Thanks Bucky for all your help and advice. I might let the system remain up and running for a couple of days before I attempt to boot with the latest kernel.

BTW, I have my system set up so I can ctl+alt+F* to a console and log in as root. Unfortunately during every freeze I've had with this problem, I have been unable to switch to a console.

And just for the record, I don't have any issues with Ubuntu. I've always been happy with the distribution since I switched from Debian years ago. If it wasn't for my photography I wouldn't even run a Windows machine.

---

### Post by Bucky Ball on 2015-12-08
> **rlovi said:**
> If it wasn't for my photography I wouldn't even run a Windows machine.

Know what you mean. I have an offline XP boot on the desktop for audio/visual stuff that I just can't equal in Ubuntu. Some things come close but I'm getting too old to have the time for the 6-12 month learning curve. :)

Keep telling myself I'll get around to it one day ...

---

### Post by rlovi on 2015-12-09
Ubuntu is my choice for audio. I have a Delta 1010LT sound card installed and use Jack, Hydrogen and Ardour. Couldn't be happier. 

I have just got so accustomed to using Photoshop and its many available plugins along with my printing software and native camera software that making it all work in a Linux environment or finding alternatives would be a monumental task. Plus my Epson R1900 printer, negative scanner and monitor calibration equipment works flawlessly in Win 10.

---

### Post by rlovi on 2015-12-10
So I got brave and booted with the latest kernel this morning. The machine booted fine and I got to the desktop. No crashes, no unusual behavior. The only problem was the nvidia drivers didn't load as it seems the nvidia module wasn't created for the kernel.

So I re-installed nvidia-355 and the module was created. I rebooted and everything was fine. The machine has been running for an hour with no hiccups.

So it seems cleaning and re-seating the ram modules solved the problem... case closed. :)

I do still have a question. Originally I was using nvidia drivers from the ppa:Xorg-edgers/ppa repository. I seem to recall that after every upgrade to a new kernel the nvida module was automatically created. Now that I recently switched to ppa:graphics-drivers/ppa, I have to manually create the module when upgrading the kernel. I just did so by just re-installing nvidia-355. Is that the correct or best way of doing so?

---

### Post by Bucky Ball on 2015-12-10
Great news! Please see the first link in my signature. It will not close the thread to future posts. (You can 'unsolve' it if the problem comes up again or if it is in a month or two post a new thread about it and include a link to this one).

As for the nvidia question, you will help your cause by posting a new thread rather than posting 18 posts deep here on a thread that is about something else. Besides which I have no idea about the answer. :D

Good luck with that.

---

### Post by rlovi on 2015-12-10
Thanks again Bucky. :)

---

### Post by Bucky Ball on 2015-12-10
Enjoy! Sometimes perfectly functional RAM sticks can be finicky. Not unusual. :D

---

