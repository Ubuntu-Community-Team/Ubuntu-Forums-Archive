---
title: "Well, my nephew borked his desktop hard"
date: 2010-03-11
forum: Testimonials &amp; Experiences
---

### Post by standingwave on 2010-03-11
He's in his thirties but relatively new to computing having just purchased a desktop (Vista) a year ago. I set him up with AVG and a couple of anti-malware programs but I'm not sure that he's been very diligent with his housekeeping. 

Anyway, he calls me up and says his computer is completely unusable. I'm thinking no big deal, we'll just boot into safe mode and run malwarebytes. Alas, the problem persists (can't run any programs including any browser, constant nagging to buy some removal tool, the usual crap - hey, at least the hardware's still working). No restore points, no recovery disc, no install discs (do OEM's even ship those anymore?) and my dear nephew is experiencing acute Internet withdrawal for the first time in his life. How quickly we become dependent.

So I'm heading over tomorrow with a Live CD of 9.10 (what a shame that this couldn't have waited  for the LTR). I intend to live boot first and see if we can recover his data (mostly music from the sounds of it) to his newly purchased external hard drive. Then, provided his hardware and cable modem check out, we intend to  install the OS.

I suspect that it won't be that big a transition for him.  I set him up a year ago with mostly open source applications so all he's ever known is Firefox, Open Office, VLC player, etc. and he uses GMail for his email so he's already got a head start over most Windows users.

Anyway, I will report back later but I expect that we will soon have another happy Ubuntu user.

---

### Post by coffeecat on 2010-03-11
> **standingwave said:**
> No restore points, no recovery disc, no install discs (do OEM's even ship those anymore?

Mostly not. :(

Over recent years I have had three laptops, 2 Sony and 1 Acer. They each came with a recovery partition. You could boot into this by pressing one of the function keys (you'd have to check the documentation to see which one) and from the recovery partition you can restore the machine to its factory state. I.e as new Windows install but without your settings, apps, updates and, most importantly, no malware. The OEM manufacturers usually do the same on their desktops, or so I believe.

It might be worth looking to see whether your nephew's machine has a recovery partition from which you could salvage Vista and then set him up with a Vista/Ubuntu dual-boot.

Also, if you can get Vista up and running again, and if it's setup the way Sony and Acer set up things, there will be a utility to burn bootable recovery DVDs.

Out of interest, what make is the desktop?

---

### Post by standingwave on 2010-03-11
Thanks for that. I've been gone from the land of MS for too long to know what OEMs are doing these days. I will look for a recovery partition when we boot it. If we can get into that, it will make things easier. He's still interested in Linux so perhaps we can set up a dual boot or Wubi.

> **coffeecat said:**
> Out of interest, what make is the desktop?It's an emachine (cost was an issue) and while I wouldn't have recommended them a few years ago, I think they've turned things around lately.

---

### Post by coffeecat on 2010-03-11
> **standingwave said:**
> It's an emachine (cost was an issue) and while I wouldn't have recommended them a few years ago, I think they've turned things around lately.

I had an emachine once. You have my sympathy. :wink:

Actually, I think you're right about turning things around. They were taken over by Acer recently (I believe) so, hopefully, it will have a similar setup to what's on my Acer laptop.

Good luck with that.

---

### Post by garvinrick4 on 2010-03-11
> **standingwave said:**
> Thanks for that. I've been gone from the land of MS for too long to know what OEMs are doing these days. I will look for a recovery partition when we boot it. If we can get into that, it will make things easier. He's still interested in Linux so perhaps we can set up a dual boot or Wubi.

It's an emachine (cost was an issue) and while I wouldn't have recommended them a few years ago, I think they've turned things around lately.
e-machines comes with a Vista OS on a disk. It is both recovery and installation. e-machines is made by Gateway. Does have a image of Vista in D drive to return to factory condition from grub.

---

### Post by standingwave on 2010-03-11
> **garvinrick4 said:**
> e-machines comes with a Vista OS on a disk. It is both recovery and installation. e-machines is made by Gateway. Does have a image of Vista in D drive to return to factory condition from grub.Gateway? OK, that makes me feel a little better. I will look for a recovery partition. Thanks.

---

### Post by standingwave on 2010-03-12
Well, the nephew took to Ubuntu just fine. We successfully recovered his data to an external drive and installed 9.10. While the files were being copied (about twenty minutes) I let him check his email, which he had been unable to for about five days.

After seeing it run on the live CD, he really wanted no more to do with Vista.

All he really uses the computer for is email and surfing the web so it's not exactly like he has unusual requirements anyway. Since he was already using Firefox (and GMail), it wasn't much of a  change at all, really.

He was suitably impressed with the start-up and shut-down  times compared with Vista. Other than that, he couldn't care less about the  OS. He just wants it to work.

---

### Post by lisati on 2010-03-12
> **standingwave said:**
>  No restore points, no recovery disc, no install discs (do OEM's even ship those anymore?) 
I had to make my own recovery disks for my main desktop (about 5 years old) and my current laptop (had for about 15 months)from the recovery partition, using software that was preinstalled. It was one of the first things I did with each machine.

---

### Post by t.rei on 2010-03-12
Weird thing:

This is a story I hear quite often:

1. <insert operating system> is broken
2. life cd to recover data (this is actually a really time-efficient way)
3. find out that all those little things like mediabuttons, touchpad scrolling, etc work 'live'
4. stick with what just works. (if the livecd sucks, go back to win!)

The here told story is probably a major way for people to get linux on their home computers, I persume. 

Happend like that to my mom, several friends, some other relatives, some customers, some of their friends... The amount of happyness it spreads when they can recover their data that would otherwise be lost to "return to factory state" is just impressive.

---

### Post by standingwave on 2010-03-12
Yeah, my nephew was impressed. I booted the Live CD (we didn't even need to change the boot order in the BIOS) and brought up Nautilus -> Computer and we could see all his drives and partitions. We quickly navigated to his windows user folder and found the folders  he wanted recovered. 

We plugged in his brand new external drive and it immediately showed up in Nautilus. We started the file transfer and then I asked him if he would like to check his email while the files were transferring. 

He was like, "We're on the Internet right now?" I said sure, and brought up Firefox. By the time he was done handling his email and the  files were done transferring, he was sold. "I want this," he said. So we went ahead and did the full install. Then I set him up with 'restricted areas' (how easy has that become in the last couple of years?!) and made sure everything (Flash, Java, codecs, etc.) were working and then we copied everything back from the Passport. While that file transfer was going, I gave him a short GNOME tutorial.

This is going to be my SOP for working on borked windows systems in the future. I have a Linux Rescue CD and could have done it all via the terminal or maybe Midnight Commander but why not give the person a little taste of the modern Linux Desktop?

---

### Post by Swagman on 2010-03-12
Even my Windows loving Big Bro now carries an Ubuntu Live Cd thanks to me.

---

### Post by coffeecat on 2010-03-12
> **standingwave said:**
> Yeah, my nephew was impressed. I booted the Live CD (we didn't even need to change the boot order in the BIOS) and brought up Nautilus -> Computer and we could see all his drives and partitions. We quickly navigated to his windows user folder and found the folders  he wanted recovered. 

We plugged in his brand new external drive and it immediately showed up in Nautilus. We started the file transfer and then I asked him if he would like to check his email while the files were transferring. 

He was like, "We're on the Internet right now?" I said sure, and brought up Firefox. By the time he was done handling his email and the  files were done transferring, he was sold. "I want this," he said. So we went ahead and did the full install. Then I set him up with 'restricted areas' (how easy has that become in the last couple of years?!) and made sure everything (Flash, Java, codecs, etc.) were working and then we copied everything back from the Passport. While that file transfer was going, I gave him a short GNOME tutorial.

This is going to be my SOP for working on borked windows systems in the future. I have a Linux Rescue CD and could have done it all via the terminal or maybe Midnight Commander but why not give the person a little taste of the modern Linux Desktop?

Wonderful story. Thanks for posting it.

My only reason for seeing if there was still a usable Vista restore partition is that your nephew had paid the Redmond tax. But great to hear of a new Ubuntu convert.

---

### Post by irishrick on 2010-03-12
I started using Ubuntu on my first laptop 3 years ago after a serious crash of xp. I inserted the live Ubuntu cd in it and recovered all my data. then I started playing with the live cd and within days decided no more xp on my laptop. Last year after struggling with the problems in vista on my desktop I again rescued everything from the drive and changed over too Ubuntu on it. I now have most of my relatives using 9.04 or 9.10 and no one misses their old OS. Glad to hear that all worked out and that your nephew is enjoying the experience.

---

### Post by standingwave on 2010-03-12
> **coffeecat said:**
> My only reason for seeing if there was still a usable Vista restore partition is that your nephew had paid the Redmond tax. But great to hear of a new Ubuntu convert.Yeah, I thought about that. But I figure he still has the registration key code and can perhaps   request a disc down the road if he needs one (no doubt for a fee, of course). But I doubt he will especially considering his relatively meager needs (web, email, iPod).

---

### Post by standingwave on 2010-03-12
> **lisati said:**
> I had to make my own recovery disks for my main desktop (about 5 years old) and my current laptop (had for about 15 months)from the recovery partition, using software that was preinstalled. It was one of the first things I did with each machine.Yeah, I think he was supposed to do so as well but never got around to it. I did that for my current machine a year ago. I was really close at that time to introducing him to Linux then. The only thing holding me back was that I wasn't all that comfortable with Linux at that time. Plus there's the warranty issue -- we've all heard the horror stories. Well, his one year warranty is just about up anyway so there's really no harm at this  point.

---

