---
title: "Sorry to say but Vista was a much better experience than Feisty..."
date: 2007-04-20
forum: Testimonials &amp; Experiences
---

### Post by etherealremnant on 2007-04-20
Its sad but its true. Installing Vista took very few steps. I put the CD in the drive, let it boot, formatted my drive, and it was automatic from there. Once I got into Windows, I ran Windows Update and it installed my sound driver for me and I got the nVidia driver off of their website. Easy!

Feisty, on the other hand, has been more of a pain than I care to imagine.

Okay so first off, my hardware:

eVGA 8800GTS (my main complaint at this point)
Intel Bad Axe 2 motherboard (everything works)
Intel Core 2 Duo E6300 @ 2.8GHz (fine)
Sound Blaster Audigy 2 ZS Platinum (fine)

Okay so here's the deal.

I put the disc in the drive, select live CD, screen goes black for a second and seems to hang. I give it a minute and the Ubuntu splash starts working (much better results than I got with the beta, which wouldn't boot on the live CD at all) so I'm thinking "okay, maybe this won't be so bad after all"

Well after a long pause, the system beeps 5 times and I'm like... wth? It seems to have frozen again... and then the CD spins back up and up comes X. Cool, we're in business.

Run the installer and get everything going, everything's fine here (though I must admit if I didn't know what I was doing or if I had multiple hard drives of the same type and size, I could have easily borked my Windows partition but that's a problem with every distro out there, it seems) and the installation proceeds.

Now the pain begins.

I reboot the computer, don't have any problems getting into X at all, and I'm thinking its smooth sailing.

Alright well I've got a nice video card, I might as well have the driver for it, right?

Well I try going into the restricted devices manager (something no n00b will ever figure out on their own and something that I think the Ubuntu devs borked on BADLY) and try enabling the nvidia driver. Everything seems okay so I reboot. Well, now I get the dreaded no screens found, blah blah blah.

I edited xorg.conf and changed it back to nv, then went into Synaptic and noticed that its using the old nVidia driver (why use the one that doesn't work with the most modern hardware?!) so I see nvidia-glx-new and install that.

I run sudo nvidia-glx-config enable and reboot.

Nope, still no GUI. Why? Because the system is still using the old nVidia kernel module. WTF?

I've tried everything I can think of from completely removing restricted everything and using the nvidia installer to every combination of things I can pull from Synaptic. Nothing works.

The Ubuntu devs, in their quest to maintain their "omg its not free, it can't be in Ubuntu... oh noes!" mentality, have SCREWED the end user and I'm honestly considering dumping Ubuntu forever and going to another distro. There is really no excuse for this. I've NEVER had such a hard time installing my 3D driver on ANY distro and I have quite a bit of Linux experience.

Great way to make it even harder for people to install the things they need, devs. We really appreciate it. I'd honestly rather use Vista than be subjected to this Ubuntu garbage anymore... and that's saying a lot.

---

### Post by Swab on 2007-04-20
> **etherealremnant said:**
> 
Great way to make it even harder for people to install the things they need, devs. We really appreciate it. I'd honestly rather use Vista than be subjected to this Ubuntu garbage anymore... and that's saying a lot.

Why do people feel the need for these ridiculous rants?  

You don't like it?  Then move on. The rest of us are doing just fine.  Nobody has subjected you to anything.

---

### Post by floke on 2007-04-20
C'mon dude, I felt like posting something similar - enjoy the DRM etc. - but lets give the guy the benefit of the doubt, we all know how frustrating Linx can sometimes be. I know absolutely kack-all about NVidia though, so can't help here - anyone else know anything?

BTW: Ranting ain't the best way to get help around here - but we'll cut you some slack since it's obviously been a real pain in the ****!

---

### Post by etherealremnant on 2007-04-20
Why do we feel the need to make these rants?

Because some of us have been loyal users of Ubuntu since the beginning and are really frustrated that we now try to get our hardware working and after trying it twenty or thirty different ways, it still doesn't work, when it always worked before!

---

### Post by Swab on 2007-04-20
> **etherealremnant said:**
> Why do we feel the need to make these rants?

Because some of us have been loyal users of Ubuntu since the beginning and are really frustrated that we now try to get our hardware working and after trying it twenty or thirty different ways, it still doesn't work, when it always worked before!

I guess there is just no accounting for 3rd party binaries...

---

### Post by finferflu on 2007-04-20
Don't forget Feisty just came out. I know it's supposed to be stable, but nobody is perfect. Maybe in a few days there will be a fix. Why don't you make it known to the devs? Other people might find help from your problem. And maybe next release it will be even better...

---

### Post by etherealremnant on 2007-04-20
It had nothing to do with the binaries.

It had to do with the way that restricted drivers are handled.

I figured it out. Where do I post a HOWTO for others that are having the same problem?

You have to edit /etc/default/linux-restricted-modules-common and in the "" for DISABLED_MODULES, you have to put nv and on top of installing build-essential, you need xserver-xorg-dev too.

But I now have full 3D accel and I'm not as pissed anymore. :lolflag:

---

### Post by finferflu on 2007-04-20
> **etherealremnant said:**
> It had nothing to do with the binaries.

It had to do with the way that restricted drivers are handled.

I figured it out. Where do I post a HOWTO for others that are having the same problem?

You have to edit /etc/default/linux-restricted-modules-common and in the "" for DISABLED_MODULES, you have to put nv and on top of installing build-essential, you need xserver-xorg-dev too.

But I now have full 3D accel and I'm not as pissed anymore. :lolflag:
In the Howtos section ;) and maybe ask the mods to make it sticky...

---

### Post by etherealremnant on 2007-04-20
Im blind. I missed that. haha.

---

### Post by floke on 2007-04-20
Well sorted!
Extremely glad it worked out for you.

PLEASE post a HOWTO

(dont know where though!)

---

### Post by etherealremnant on 2007-04-20
There's no HOWTO section that I see? Unless I really AM blind... lol

Maybe I should post it in the hardware section?

---

### Post by Swab on 2007-04-20
The funny thing is I am having a similar issue.  My crappy card apparently now needs the legacy driver.  But it wasn't working for me (no composite) so I installed an older version from the nvidia site.. but then X wouldn't start stating there was some kind of version conflict between the module and umm something else.

---

### Post by finferflu on 2007-04-20
> **etherealremnant said:**
> There's no HOWTO section that I see? Unless I really AM blind... lol

Maybe I should post it in the hardware section?
Ah they've changed its name, now it's called Tutorials & tips: [http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)
That's where I see all the howtos...

---

### Post by etherealremnant on 2007-04-20
Yup. That's the restricted drivers for ya.

edit the linux-restricted-modules-common file that I posted about and add nv there, reboot, and try it again.

---

### Post by Swab on 2007-04-20
I don't see how that will help my situation... I'll give it a go later.

---

### Post by etherealremnant on 2007-04-20
Its probably conflicting between the two modules, especially if you used apt to install one of Ubuntu's nvidia packages and then used nvidia's legacy driver from their website. Though in your case, I think you'd have to type nvidia_legacy instead of nv.

---

### Post by Swab on 2007-04-20
> **etherealremnant said:**
> Its probably conflicting between the two modules, especially if you used apt to install one of Ubuntu's nvidia packages and then used nvidia's legacy driver from their website. Though in your case, I think you'd have to type nvidia_legacy.

Yeah, worth a try.  Thanks

---

### Post by Visceral Monkey on 2007-04-20
8800gts here and same problems. I finally gave up after 3 installs. Installed Sabayon  linux and it worked out of the box the first time.

I'm still looking for a how-to for ubuntu and 8800s though, so thats good news at least.

---

### Post by etherealremnant on 2007-04-20
It works 100% now.

Sabayon doesn't like my ethernet chip. I tried it and it failed. And I like Gnome more than KDE anyway.

---

### Post by hendoc on 2007-04-21
Give Vista 6 months and if everything still works fine, you can say "I told you so."  Until then, I wouldn't talk too loud.

---

### Post by MontyV on 2007-04-21
> **etherealremnant said:**
> There's no HOWTO section that I see? Unless I really AM blind... lol

Maybe I should post it in the hardware section?

Any luck on the HOWTO?  I was a bit frustrated when I ran into problems with Ubuntu a year back and went with a more slimmed down distro.  I'm back and want to try Ubuntu again but started reading problems with the Nvidia 8800gts.  It seems like you figured it out.  Can't wait for your HOWTO.

- Monty

---

### Post by DarkStarAeon on 2007-04-22
etherealremnant, I do understand, but...

 Ask yourself this, once you got past the install of Windows or Ubuntu (any version) which was more stable, more secure, and cheaper to own and operate?

I have to admit, I have vented my frustrations a few times on forums of different distros, including this one, and I will also admit that I am not, never have been, and probably never will be a patient person. I try, but it's against my nature. 

I have to remind myself that any problem I encounter with Ubuntu, or any Linux distro really, is a problem that I didn't pay for. Any upgrade I get, I didn't pay for. Any improvements to the software that make my life easier, I didn't have to pay for.
With Microsoft you pay a ridiculous amount of money to tear your hair out when something does go wrong.
Sure, I'll admit, there are some things about Windows that are nice, and do work well, but when something does go wrong with Windows it usually goes really really wrong, and is usually a problem that takes a lot of time to fix...if it can be fixed.

When you have a problem with something on Ubuntu, within minutes you can usually find the answer on the forums. One of the best things anyone can do is use the search feature on the message board, chances are, the answer is there.

Even if you have to replace a piece of hardware to make something compatible on your machine to be happy running linux, it's still usually cheaper than  just buying a copy of Windows. And with Vista many had to buy a copy and still upgrade hardware.

Just repeat my mantra...it's free, it's free, it's free. lol

---

