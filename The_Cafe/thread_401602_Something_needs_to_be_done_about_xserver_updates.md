---
title: "Something needs to be done about xserver updates"
date: 2007-04-04
forum: The Cafe
---

### Post by FuturePilot on 2007-04-04
A while back I had the unfortunate experience of an xserver-xorg update completely breaking my system. And no I wasn't using the Nvidia drivers, I was using the nv ones. And now I saw that there was another xserver-xorg update today and decided to come here to see if it was safe to install it. And I noticed that tons of other people are having a problem with xserver crashing when trying to run the screensaver or any 3D acceleration. The exact same thing that happened to me. So why is it so hard to implement a xserver update? It's kind of nerve rattling to think that the next update could break your system. Luckily everything went fine for me this time, but there's a bunch of other people with a broken system now.

---

### Post by plb on 2007-04-04
Don't worry, soon enough we will have bulletproof X...I believe in Feisty +1 or the next release.

---

### Post by FuturePilot on 2007-04-04
> **plb said:**
> Don't worry, soon enough we will have bulletproof X...I believe in Feisty +1 or the next release.

But the bulletproof X had to do with Xserver starting no matter what. This isn't an issue of Xserver starting, but an issue of applications crashing it to GDM.

---

### Post by DoctorMO on 2007-04-04
The problem with Xorg is that after the fork the project had to rally and it took time and energy to sort. Imagen if an important part of your os got dissolved and had to start by forking. nasty business the whole thing.

Now add to that the fact that two companies have internal problems and control an entire aspect of the functionality (nvidia/ati) and you have to program around this lump of digestive secretion and still end up with a working xorg on all machines.

If you think it can be done better your welcome to fork xorg or ubuntu; I know this sounds like a shut up or do something argument but that really is the only option since your not willing to give the new xorg devs the benefit of doubt.

---

### Post by deadfred_10 on 2007-04-04
I had the same problem with the update breaking my system and yes I am using the real Nvidia drivers. This update didn't break the system but now when the screen saver comes on I get logged out and and have to login again. When I try to turn off the screen saver, I can't because it does the same thing when the small view of the screen saver starts. You may want to turn off the screen saver before you do the update.

---

### Post by maniacmusician on 2007-04-04
> **DoctorMO said:**
> The problem with Xorg is that after the fork the project had to rally and it took time and energy to sort. Imagen if an important part of your os got dissolved and had to start by forking. nasty business the whole thing.

Now add to that the fact that two companies have internal problems and control an entire aspect of the functionality (nvidia/ati) and you have to program around this lump of digestive secretion and still end up with a working xorg on all machines.

If you think it can be done better your welcome to fork xorg or ubuntu; I know this sounds like a shut up or do something argument but that really is the only option since your not willing to give the new xorg devs the benefit of doubt.
I think that in this case, it's probably more of a matter of updates being thoroughly tested before being made available to thousands of people. 

I personally haven't had any problems with xserver updates, ever. I guess I got lucky.

---

### Post by FuturePilot on 2007-04-04
It's not that I'm not giving the xorg devs a chance, I'm really just wondering why this is still happening. It happened to me 9 months ago and now it's happening again. But I guess you kind of answered my question.

---

### Post by Polygon on 2007-04-04
its not entirely xorg's fault. They have to deal with video cards that mostly have closed source drivers, so they have to reverse engineer and kinda guess/predict how things are going to work.

if ati/nvidia had open source drivers, trust me this problem would not exist, but sadly that is not the case.

and if your afraid of an xorg update is going to break something, just dont install it.

---

### Post by DoctorMO on 2007-04-04
> just wondering why this is still happening

Digestive secretion happens.

---

### Post by FuturePilot on 2007-04-04
> **DoctorMO said:**
> Digestive secretion happens.:lolflag: We do need some open source drivers though. I'm guessing that black window bug would have been gone a long time ago if they were open source.

---

### Post by macogw on 2007-04-05
When X dies, it's 3rd party drivers needing to be reinstalled

I use Intel, though, so I've only ever had one issue with X and that was during the merging in of Xorg 7.2 without libmesa which broke Beryl (but not X)

---

### Post by prizrak on 2007-04-06
Dude you are using Feisty, Feisty is beta, beta will break. See where I'm going? BTW I haven't had a single X problem since Feisty Herd 2 and I'm using the "bad" nVidia driver.

---

### Post by FuturePilot on 2007-04-06
I'm only using Feisty on my laptop not on the main computer. That one is running Dapper and it broke with the last updates about 9 months ago and I was using the nv drivers.

---

### Post by prizrak on 2007-04-06
> **FuturePilot said:**
> I'm only using Feisty on my laptop not on the main computer. That one is running Dapper and it broke with the last updates about 9 months ago and I was using the nv drivers.

Upgrade to Feisty? Also last I checked the nv driver doesnt' support 3D

---

### Post by macogw on 2007-04-06
> **FuturePilot said:**
> I'm only using Feisty on my laptop not on the main computer. That one is running Dapper and it broke with the last updates about 9 months ago and I was using the nv drivers.

You mean the blackout in August?  linux-restricted-modules didn't hit the repos on time.  Always check that l-r-m is there before letting a new kernel be installed.  If you forget, boot the old kernel.  That happened on Feisty with 2.6.20-13 too, but I don't think anyone cared too much given that we're running unstable and therefore probably can stomach spending some time in the TTY.  I think with -14 l-r-m came through before the kernel did.  At least I think I saw it in my /var/cache/apt/archives/ yesterday when the kernel came through today.  If that's what happened, that sounds like a good way to handle it to me.

---

### Post by FuturePilot on 2007-04-06
That was back when I was new to Linux. I didn't even know Nvidia provided accelerated drivers for Linux. And I didn't even know about Beryl. But now I use the Nvidia drivers. And I tried the older kernels and everything was still crashing me back to gdm.

---

### Post by mrazster on 2007-04-06
Well I have been running Fiesty since *Herd2* and I've been running the nvidia 1.0.9755 from the repos. all along. It has been a couple of xorg updates anlong with kernel an driver updates and it hasn't broke once. If anything it has gotten more stable.
So I don't it I have just had luck or if the update process in Feisty has actually been "fixed/worked out"...but it works flawlessly, atleast for me.

---

### Post by forrestcupp on 2007-04-06
Well, I'm using Feisty beta with proprietary nvidia drivers.  My problem wasn't with the x-server update, it was with the kernel update.  Just now, Ubuntu updated my kernel to 2.6.20-14-386, but it didn't update the linux-restricted-modules.  Why?  The correct restricted modules is in the repos, but it didn't update that too, and it caused me to not be able to start x.  Luckily, I knew to restart with a prior kernel and install the updated restricted modules manually, but if I didn't know to do that, I'd be screwed right now.  So my question is, if they have it available and they are going to update the kernel, why wouldn't my restricted modules be updated too?

---

### Post by prizrak on 2007-04-06
> **forrestcupp said:**
> Well, I'm using Feisty beta with proprietary nvidia drivers.  My problem wasn't with the x-server update, it was with the kernel update.  Just now, Ubuntu updated my kernel to 2.6.20-14-386, but it didn't update the linux-restricted-modules.  Why?  The correct restricted modules is in the repos, but it didn't update that too, and it caused me to not be able to start x.  Luckily, I knew to restart with a prior kernel and install the updated restricted modules manually, but if I didn't know to do that, I'd be screwed right now.  So my question is, if they have it available and they are going to update the kernel, why wouldn't my restricted modules be updated too?

Weird for me the updater didn't even show the new kernel till all of the parts were up. Synaptic had it in there though.

---

### Post by Crypto-138 on 2007-04-06
> **macogw said:**
> When X dies, it's 3rd party drivers needing to be reinstalled

I use Intel, though, so I've only ever had one issue with X and that was during the merging in of Xorg 7.2 without libmesa which broke Beryl (but not X)

That was great advice. I had suspected it was the nVidia driver, but I wasn't too sure until I read you post. 

My PC froze while running ReactOS on QEMU, and I thought some Gnome library became corrupt, while the disk was writing. After going through the hassle of installing Xfce and having that fail as well, I xterm'd into firefox and read that comment above. ](*,) 

Good thing I keep the nVidia installer in my home directory. This is the third time this week I've had to install the nVidia driver.

---

### Post by macogw on 2007-04-06
> **prizrak said:**
> Weird for me the updater didn't even show the new kernel till all of the parts were up. Synaptic had it in there though.

Same here.  Looking in /var/cache/apt/archives, the kernel source was downloaded on Tuesday.

---

