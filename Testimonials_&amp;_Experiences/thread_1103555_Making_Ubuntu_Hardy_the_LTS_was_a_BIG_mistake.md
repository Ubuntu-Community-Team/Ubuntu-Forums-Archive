---
title: "Making Ubuntu Hardy the LTS was a BIG mistake"
date: 2009-03-22
forum: Testimonials &amp; Experiences
---

### Post by MYGRA1N on 2009-03-22
They should have made Intrepid the LTS release instead.

I've just tried to reinstall Hardy on my pc as xp has died its millionth death. All goes fine in installing from the cd. Then I reboot, wait for it to tell me theres updates, download the updates but oh "dkps cannot lock the SOMETHING" whutevathehellthatmeans. So I click close and try again and it works. I reboot, goto hardware drivers and oh theres no nVidia driver??
So I google and find out that that driver dosen't support my card. So it's off to nVidias site to download the latest driver. I try to install but oh I need libc development package. So boot back into GDM/gnome and download it from synaptic and reboot. then I install via sudo /etc/init.d/gdm stop method(which always works perfectly on Intrepid, and it goes fine until I reboot to be met by the stupid low graphics loop!!

Arghhhhhhhhhhhhh, do canonical not think about these things?? Why don't they update the graphics driver options in the Hardware Drivers section. if your going to make something LTS then surely it isn't so hard to realise that you have to keep up on the driver side of things! And another thing why don't they ever upgrade the packages in the repositories?? VLC/Brasero etc are all way out of date. they really should put more thought into supporting what they've already released instead of chasing the stupid 6 month cycle thing!

---

### Post by z.s.tar.gz on 2009-03-22
You don't make any sense. Don't like 8.04? Don't use it.

Long Term Support != Long Term Hardware Compatibility

The End

---

### Post by MYGRA1N on 2009-03-22
> **z.s.tar.gz said:**
> You don't make any sense. Don't like 8.04? Don't use it.

Long Term Support != Long Term Hardware Compatibility

The End

The end nothing. I wanted to install Hardy for the exact reason that its supported for 3 years. Having to upgrade every 6 months just to keep up to date is getting pretty tedious. And your "
Long Term Support != Long Term Hardware Compatibility" makes no sense to me. There ISNT long term hardware support if you have a graphics card that's newer than the distro. The fact that the default driver in Hardy is woefully out of date kind of shows that.

---

### Post by wolfen69 on 2009-03-22
do you think that because it doesn't work for you that everyone has those issues? what made your computer the gold standard by which all OS's are judged?

millions of people use it without issue.

there are thousands of hardware combinations and other factors that determine if a particular distro will work on it. if it doesn't work for you, that's OK. but to say it's junk because it doesn't work on 1 computer out of millions is ridiculous.

chill out and just use what works for *your* particular hardware combination.

when you work on 100's of different computers and gain a little tech savvy, you realize that no OS is perfect on all computers. i've seen vista fail on computers it was supposedly designed for. i've seen xp freak out for no apparent reason, while win2000 worked just fine. the same goes for hardy. it is impossible for any distro or OS for that matter to work on everything.

i'll ask again, what makes your computer the standard by which an OS is judged?

how come we don't use *my* computer as that standard? if we could, i would say hardy is perfect because it runs perfect on my computer. see where this is going?

---

### Post by MYGRA1N on 2009-03-22
> **wolfen69 said:**
> do you think that because it doesn't work for you that everyone has those issues? what made your computer the gold standard by which all OS's are judged?

millions of people use it without issue.

there are thousands of hardware combinations and other factors that determine if a particular distro will work on it. if it doesn't work for you, that's OK. but to say it's junk because it doesn't work on 1 computer out of millions is ridiculous.

chill out and just use what works for *your* particular hardware combination.

when you work on 100's of different computers and gain a little tech savvy, you realize that no OS is perfect on all computers. i've seen vista fail on computers it was supposedly designed for. i've seen xp freak out for no apparent reason, while win2000 worked just fine. the same goes for hardy. it is impossible for any distro or OS for that matter to work on everything.

i'll ask again, what makes your computer the standard by which an OS is judged?

how come we don't use *my* computer as that standard? if we could, i would say hardy is perfect because it runs perfect on my computer. see where this is going?

Lol, yes I see your point very clearly, but I don't think you see mine. My main problem isn't with how the distro works. Its the simple fact that Hardy won't support my graphics card because the default driver is painfully outdated!

And just out of curiousity can you install the latest nVidia driver on a Hardy installation on your machine?? As we have exactly the same type of graphics card.

---

### Post by wolfen69 on 2009-03-22
> **MYGRA1N said:**
> 
And just out of curiousity can you install the latest nVidia driver on a Hardy installation on your machine?? As we have exactly the same type of graphics card.

yes, you can. i'm using the nvidia 177 drivers and they work great.

---

### Post by MasterNetra on 2009-03-22
Non-LTS versions have 18 month support from release... I don't see what the problem is.

---

### Post by jbysmith on 2009-03-22
Exactly, Wolfen69 sums it up nicely.  About the only platform you're guaranteed to have 100% success with is a game console, a Mac, and other toys.  It's the manufacturer's hardware and no third party stuff, so yea it'll work.

Not just specific to Linux too of course, anyone who has driver issues with Vista will tell you the same thing, Vista obviously sucks because it won't run on their hardware.  (Ok, we all know Vista sucks but you get my point.)  

Different distros manage hardware differently too; if Ubuntu's not working for you, pick a different one.  Plenty of quality ones to pick.  For *my* particular hardware Arch has always done a stellar job with the hardware support. Ubuntu's been pretty good, along with PCLinuxOS Gnome.  Fedora for whatever reason gives me problems. On this same system I've had nothing but hardware issues with BSD.  I certainly won't say BSD or Fedora sucks, as they run beautifully on some other systems I have.

Or yes, just go with a non-LTS build.  8.10's been working better, and 9.04 is looking *really* good, even in its alpha state.  I also have one older system that's still running 7.04, and another with Windows 2000, just because I can.

---

### Post by MYGRA1N on 2009-03-22
177 aren't the latest but its still better than 169. How did you install them as everyway I've tried just ***** up.:(

---

### Post by Sarai the Geek on 2009-03-23
> **jbysmith said:**
> About the only platform you're guaranteed to have 100% success with is a game console, a Mac, and other toys.

Hah... hah hah. I had a mac and I can attest to the fact that they are not a guaranteed success either. Which is kind of sad when you think about it.

Not to derail the thread into a mac-hating flamewar. I liked that computer a lot (still have it, in fact), but I went into it expecting a computer that I didn't have to fight with- which I should have known was a pipe dream. At least when I have problems with Ubuntu I can fix most of them myself and when I can't I know exactly where to go for help. ;)

---

### Post by jbysmith on 2009-03-23
> **Sarai the Geek said:**
> Hah... hah hah. I had a mac and I can attest to the fact that they are not a guaranteed success either. Which is kind of sad when you think about it.

Huh kinda surprised to hear that.  I guess I missed the commercial where the guy goes "Hi I'm a Mac, and I don't run on my own hardware."  Weird that.

> **MYGRA1N said:**
> 177 aren't the latest but its still better than 169. How did you install them as everyway I've tried just ***** up.:(

I think I had the same issue with the 180 drivers in 8.04 too if I remember right.  Only system I have 8.04 on now is a server with no GUI, so can't say for sure.  I do recall getting stuck in that "low resolution" issue too though.  I've since moved on from 8.04 on a desktop environment though, don't remember if I got around it or not.  Currently using Arch, and really enjoying Jaunty 9.04, which includes the 180 series of nVidia drivers by the way.. most likely switching once it goes official.

Have you checked your logs?  Might be a clue in there as to why the nvidia module isn't starting.  (Another thing I love about Linux.. the logs are actually useful, not filled with stuff like "Event 3921" and the description box is empty..)

---

### Post by Tamlynmac on 2009-03-23
I don't understand it either. Why doesn't Ubuntu work with every piece of hardware ever made. What's wrong with Canonical anyway. One would think they have enough influence to force all hardware mfgs. to write drivers for Ubuntu. Or why don't they simply hire a huge staff to perform this task. ;)

Seriously, shouldn't one investigate compatibility prior to installation? If your aware of an incompatibility issue prior to installation then why install it? Simply continue to use a version that works and enjoy the free OS. I still don't understand this incessant need to upgrade at all costs. Spend time identifying that your hardware is compatible with the upgrade and said upgrade has features that you require. The next LTS will soon be released and I suspect it will receive similar complaints as every release has in the past. I've noticed that even after the LTS releases, some continue experiencing problems until it's updated. Patience, is the key to performance. In my opinion one should relax and take time to investigate the new release prior to installing it. I'll bet it reduces your frustration level immensely.

I must agree with wolfen69: 
 > it is impossible for any distro or OS for that matter to work on everything.
 
Not all systems are going to play well with every version of Ubuntu. I would suggest you accept that fact or use a different OS. Simply, use what works as it's only an operating system and shouldn't be considered a life or death decision. When wolfen69 points out the obvious (your system is not the standard for judging Ubuntu), he's on target - in my opinion. When considering the vast number of different system hardware configurations possible, the concept that one device on your system has a driver issue - doesn't automatically equate to a defect in the OS. 

I would also suggest you take a moment and notify NVIDIA, as they're responsible for the product. I often wonder how they would respond to a communication similar to the one you posted here?

---

### Post by MYGRA1N on 2009-03-23
> **Tamlynmac said:**
> I don't understand it either. Why doesn't Ubuntu work with every piece of hardware ever made. What's wrong with Canonical anyway. One would think they have enough influence to force all hardware mfgs. to write drivers for Ubuntu. Or why don't they simply hire a huge staff to perform this task. ;)

Seriously, shouldn't one investigate compatibility prior to installation? If your aware of an incompatibility issue prior to installation then why install it? Simply continue to use a version that works and enjoy the free OS. I still don't understand this incessant need to upgrade at all costs. Spend time identifying that your hardware is compatible with the upgrade and said upgrade has features that you require. The next LTS will soon be released and I suspect it will receive similar complaints as every release has in the past. I've noticed that even after the LTS releases, some continue experiencing problems until it's updated. Patience, is the key to performance. In my opinion one should relax and take time to investigate the new release prior to installing it. I'll bet it reduces your frustration level immensely.

I must agree with wolfen69: 
 
Not all systems are going to play well with every version of Ubuntu. I would suggest you accept that fact or use a different OS. Simply, use what works as it's only an operating system and shouldn't be considered a life or death decision. When wolfen69 points out the obvious (your system is not the standard for judging Ubuntu), he's on target - in my opinion. When considering the vast number of different system hardware configurations possible, the concept that one device on your system has a driver issue - doesn't automatically equate to a defect in the OS. 

I would also suggest you take a moment and notify NVIDIA, as they're responsible for the product. I often wonder how they would respond to a communication similar to the one you posted here?

My problem with Hardy and Canonical is based on the fact that the driver is so stupidly out of date. I forgot that when I used Hardy before I was using ATi, and their drivers are actually very easy to install, even if they where as glitched up as hell. I wish nVidia's driver's where as straight forward.

---

### Post by zero244 on 2009-03-23
The 177 drivers dont work for me but the 173 drivers do.
I might recommend installing Envyng using it to uninstall your current drivers then install the latest drivers using envyng.
About the only hardware problem Ive had with Linux is video drivers.
With Video drivers you dont need the latest version.
You just need the video drivers that work with your machine.
Good luck.
By the way Im running Hardy and it works perfectly.
Since its working great right now Ive stopped doing updates.
Updates can break things so if you get everything running smooth you might consider not doing further updates.
I stopped doing updates with Windows XP after SP1 as well.

---

### Post by MYGRA1N on 2009-03-23
> **zero244 said:**
> The 177 drivers dont work for me but the 173 drivers do.
I might recommend installing Envyng using it to uninstall your current drivers then install the latest drivers using envyng.
About the only hardware problem Ive had with Linux is video drivers.
With Video drivers you dont need the latest version.
You just need the video drivers that work with your machine.
Good luck.
By the way Im running Hardy and it works perfectly.
Since its working great right now Ive stopped doing updates.
Updates can break things so if you get everything running smooth you might consider not doing further updates.
I stopped doing updates with Windows XP after SP1 as well.

Oh yeah thanks I forgot about ENVY, but that's still not really any use to me. I use WINE quite extensively and believe me with any driver pre 177 you run into all kinds of trouble.

And not updating WindowsXP? damn your brave!

---

