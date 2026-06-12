---
title: "Why I Love Linux"
date: 2008-12-07
forum: Testimonials &amp; Experiences
---

### Post by Greyed on 2008-12-07
With all the whinging going on in here I figured it's high time to post something positive.  Note that this is a repost of a [blog]("http://greydmiyu.blogspot.com/2008/12/why-i-love-linux.html") entry I just posted about 2 minutes go but it fits here.  :)

Thanks to my father I came into possession of a relatively new Abit NF-M2S motherboard with an AMD 4800+ X2 dual-core 64bit CPU on board. As this is decidedly faster than my MSI K7N2 w/AMD 2500+ single-core 32bit CPU I decided to drop my new motherboard into my machine. That machine has a 200Gb drive with ~175Mb carved out for WinXP SP3 and ~25Gb for [KUbuntu]("http://www.kubuntu.org/") 8.10.  Once the boards were swapped and all the cables hooked back up I decided to boot the machine.

First up, WinXP. Surprisingly it actually booted with video. I got to the login screen and then, nothing. It didn't recognize my mouse nor my keyboard. Both were plugged in as USB devices. I decided to swap my keyboard over to the PS/2 connector. No go. WinXP just sat there totally non-interactive. It wasn't locked, it just wasn't responding to my input.

So I decided to boot into KUbuntu. About 1 second into the boot process the machine shut down. Several more attempts with the same results. BIOS changes made, same results. Stepping down to older kernels, same results. Boot after boot the machine just shut off at the same point.

Now, I know this sounds like Linux is failing. Those who know me know this is a setup. The problem was me banging my head against the wall instead of taking 2-steps over and walking through the doorway. The 2 steps? Hit e on [Grub]("http://www.gnu.org/software/grub/") to edit the boot lines and remove the "splash" and "quiet" options. Hit b for boot and watch the boot messages. Once KUbuntu started initializing the USB subsystem the machine reset. Start up, go into the BIOS, step USB from 2.0 & 1.1+ to just 1.1+ and KUbuntu booted just fine.

Keyboard found. Video found. Ethernet card found. Sound wasn't found but I'm not sure I have it enabled. Might be fighting with my SB Live! XGamer if it is. I check my email, poke at [Ubuntuforums]("http://ubuntuforums.org/") then decide to try WinXP again now that I know the USB was a tad flaky.

WinXP booted up fine. Found the keyboard and mouse. Video is slow and ethernet non-functional. No sound, either. I was able to log in. I got several new hardware wizards. None of them were able to resolve since the third in line was the ethernet card and all of them, even the ethernet card, wanted to go out to the internet to obtain drivers. No problems, I have an Ext3 driver on WinXP, just reboot to KUbuntu, download the drivers, boot back into WinXP, pull them over and install.

The KUbuntu portion ran fine. However upon rebooting to WinXP it BSOD after I logged in. Even worse, I hit the reset button and my hard drive on longer is recognized by the motherboard! A quick power-cycle and the hard drive came back. Tried it once more, same results. After a second power-cycle to get the hard drive recognized again I decided to reboot into KUbuntu. If I succeeded I figured it would make a great "Why I Love Linux" blog post since it was Linux that enabled me to identify the problem and Linux that booted perfectly the first time. You know the outcome, you're reading it. ;)

---

### Post by solwic on 2008-12-07
> **Greyed said:**
> With all the whinging going on in here I figured it's high time to post something positive.  Note that this is a repost of a [blog]("http://greydmiyu.blogspot.com/2008/12/why-i-love-linux.html") entry I just posted about 2 minutes go but it fits here.  :)

Thanks to my father I came into possession of a relatively new Abit NF-M2S motherboard with an AMD 4800+ X2 dual-core 64bit CPU on board. As this is decidedly faster than my MSI K7N2 w/AMD 2500+ single-core 32bit CPU I decided to drop my new motherboard into my machine. That machine has a 200Gb drive with ~175Mb carved out for WinXP SP3 and ~25Gb for [KUbuntu]("http://www.kubuntu.org/") 8.10.  Once the boards were swapped and all the cables hooked back up I decided to boot the machine.

First up, WinXP. Surprisingly it actually booted with video. I got to the login screen and then, nothing. It didn't recognize my mouse nor my keyboard. Both were plugged in as USB devices. I decided to swap my keyboard over to the PS/2 connector. No go. WinXP just sat there totally non-interactive. It wasn't locked, it just wasn't responding to my input.

So I decided to boot into KUbuntu. About 1 second into the boot process the machine shut down. Several more attempts with the same results. BIOS changes made, same results. Stepping down to older kernels, same results. Boot after boot the machine just shut off at the same point.

Now, I know this sounds like Linux is failing. Those who know me know this is a setup. The problem was me banging my head against the wall instead of taking 2-steps over and walking through the doorway. The 2 steps? Hit e on [Grub]("http://www.gnu.org/software/grub/") to edit the boot lines and remove the "splash" and "quiet" options. Hit b for boot and watch the boot messages. Once KUbuntu started initializing the USB subsystem the machine reset. Start up, go into the BIOS, step USB from 2.0 & 1.1+ to just 1.1+ and KUbuntu booted just fine.

Keyboard found. Video found. Ethernet card found. Sound wasn't found but I'm not sure I have it enabled. Might be fighting with my SB Live! XGamer if it is. I check my email, poke at [Ubuntuforums]("http://ubuntuforums.org/") then decide to try WinXP again now that I know the USB was a tad flaky.

WinXP booted up fine. Found the keyboard and mouse. Video is slow and ethernet non-functional. No sound, either. I was able to log in. I got several new hardware wizards. None of them were able to resolve since the third in line was the ethernet card and all of them, even the ethernet card, wanted to go out to the internet to obtain drivers. No problems, I have an Ext3 driver on WinXP, just reboot to KUbuntu, download the drivers, boot back into WinXP, pull them over and install.

The KUbuntu portion ran fine. However upon rebooting to WinXP it BSOD after I logged in. Even worse, I hit the reset button and my hard drive on longer is recognized by the motherboard! A quick power-cycle and the hard drive came back. Tried it once more, same results. After a second power-cycle to get the hard drive recognized again I decided to reboot into KUbuntu. If I succeeded I figured it would make a great "Why I Love Linux" blog post since it was Linux that enabled me to identify the problem and Linux that booted perfectly the first time. You know the outcome, you're reading it. ;)

Don't you have to reinstall Windows when you switch out major hardware like that?  Might explain why Windows kept failing.  

Anyway, great to hear a success story.  I'd imagine this is a lot more common than we hear about, too.  I know several times I've used Ubuntu to fix my Win XP (when I had it; straight Ubuntu now), or used a LiveCD to diagnose/repair a friend's Win XP.

:)

---

### Post by Comhra on 2008-12-07
Linux and *nix systems generally are a constant source of amazement for me and they keep getting better.

---

### Post by Greyed on 2008-12-07
> **jrock612 said:**
> Don't you have to reinstall Windows when you switch out major hardware like that?  Might explain why Windows kept failing.

Generally, yes.  But of course that's kind of the unsaid point of my message.  I probably will have to figure out how to reinstall WinXP, and all my apps, just to get it viable again.  Linux worked.  For all the belly-aching the Windows world says about the difficulty of Linux installs it is amazing how horrible Windows holds up in the exact same arena.

> Anyway, great to hear a success story.  I'd imagine this is a lot more common than we hear about, too.  I know several times I've used Ubuntu to fix my Win XP (when I had it; straight Ubuntu now), or used a LiveCD to diagnose/repair a friend's Win XP.

I wish I could just say fuggit to XP, move all my data over to KUbuntu and just have it take over my HD.  It would simplify my life.  Unfortunately Blizzard, Valve and a few other gaming companies have me by the short-hairs when it comes to that particular decision.  *sigh*

---

### Post by solwic on 2008-12-07
> **Greyed said:**
> I wish I could just say fuggit to XP, move all my data over to KUbuntu and just have it take over my HD.  It would simplify my life.  Unfortunately Blizzard, Valve and a few other gaming companies have me by the short-hairs when it comes to that particular decision.  *sigh*

I wish I could get Kubuntu to work for me :(  Gnome is OK, but I always liked the look of KDE.  Unfortunately (the last time I looked, anyway) KDE 4.x is horribly, terribly, embarrassingly broken, and 3.whatever just doesn't look as good as 4.  

Or have they made any progress there?  It's been a few months since I last looked....

But yeah, the idea is the same.  It's really nice to be totally Ubuntu.  I have Win Xp installed in VirtualBox, of course, but I never use it.  It's just there in case I need a reminder of how great Ubuntu is by comparison.  :)

---

### Post by Greyed on 2008-12-07
> **jrock612 said:**
> I wish I could get Kubuntu to work for me :(  Gnome is OK, but I always liked the look of KDE.  Unfortunately (the last time I looked, anyway) KDE 4.x is horribly, terribly, embarrassingly broken, and 3.whatever just doesn't look as good as 4.  

Or have they made any progress there?  It's been a few months since I last looked....

Give it another try.  I was extremely critical of KDE 4.0.  It's a good thing I was venting away from the developers because I was not kind in my choice of words.  However when 4.1 came out I started working in 4.1 almost exclusively on my VM.  It was tolerable.  Many of the issues I had with 4.0 had been addressed.

Currently my VM (and real home machine mentioned in the original post) are on 4.2b1 and I couldn't imagine going back to 3.9.10.  Not that 3.9.10 is bad.  It is solid.  But 4.2 is looking to be pretty solid and polished.  If you've not given it a try since 4.0 I'd say make a small VM, install KUbuntu to 4.1 then update to 4.2 and give it another whirl.

---

### Post by solwic on 2008-12-07
> **Greyed said:**
> Give it another try.  I was extremely critical of KDE 4.0.  It's a good thing I was venting away from the developers because I was not kind in my choice of words.  However when 4.1 came out I started working in 4.1 almost exclusively on my VM.  It was tolerable.  Many of the issues I had with 4.0 had been addressed.

Currently my VM (and real home machine mentioned in the original post) are on 4.2b1 and I couldn't imagine going back to 3.9.10.  Not that 3.9.10 is bad.  It is solid.  But 4.2 is looking to be pretty solid and polished.  If you've not given it a try since 4.0 I'd say make a small VM, install KUbuntu to 4.1 then update to 4.2 and give it another whirl.

It's updating in VirtualBox right now.  :)  I think I'll give it a week or two of use and see how I like it.  If it's good, I may just switch.  

What I won't do is try to add KDE to my current install.  I've been down that road before...not pretty at all.  :(

Anyway, guess we'll see how it goes....  :cool:

---

### Post by stalkingwolf on 2008-12-08
> Don't you have to reinstall Windows when you switch out major hardware like that? 
My experience is yes.  However i recently had to change out a MB that went bad. I was totally surprised when xp booted and ran with no problems.  The
specs between the 2 boards must have been close enough to satisfy windoz.

---

### Post by halovivek on 2008-12-08
i love because to do some experiment in that ....

---

### Post by chongzi889 on 2008-12-08
sluice valve is **[gate valve](http://www.valvesupplier.net/index.htm)** also,as it is sometimes known, is a valve that opens by lifting a round or rectangular gate/wedge out of the path of the fluid. The distinct feature of a [gate valve]("http://www.valvesupplier.net/index.htm") is the sealing surfaces between the gate and seats are planar.

---

