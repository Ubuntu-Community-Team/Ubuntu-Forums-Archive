---
title: "Ten sticking points for new Ubuntu users. Do you agree?"
date: 2009-03-14
forum: The Cafe
---

### Post by sulekha on 2009-03-14
Hi all,


See the link :- 

  [http://www.thinkdigit.com/forum/archive/index.php/t-91856.html]("http://www.thinkdigit.com/forum/archive/index.php/t-91856.html")

---

### Post by sulekha on 2009-03-14
Hi all,

see this:- 

 [http://www.thinkdigit.com/forum/archive/index.php/t-91856.html]("http://www.thinkdigit.com/forum/archive/index.php/t-91856.html")

---

### Post by perrti-y02 on 2009-03-14
With the point about the display, I find that it will work with whatever display you install it on. Change display and everything breaks but if you keep the hardware the same then it is happy.

---

### Post by blueshiftoverwatch on 2009-03-14
> **from the link said:**
> 
Ubuntu is still bad at properly detecting and setting up the display. Once it's gone wrong, there isn't much you can do from the GUI setup tool -- it either lies about your screen settings or offers inappropriate screen modes. Anyone for 640x480@52Hz on a 19-inch CRT?
The only way I was able to get my resolution to stay where I have it set at (1600x1200) and not revert back to one of the lowest resolution settings possible every so many times I restarted the computer was to set my resolution with Nvidia's proprietary program [nvidia-settings]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-t.html") which changes things around in my xorg.conf file instead of being able to set it the default way by going to System > Preferences > Screen Resolution.

---

### Post by Yashiro on 2009-03-14
Most points there are pretty superficial but they do exist and annoy some people.

---

### Post by chris4585 on 2009-03-14
here's a driect link to the actual article and not just a forum

[http://www.linux.com/feature/139214]("http://www.linux.com/feature/139214")

---

### Post by pbpersson on 2009-03-14
I was trying to setup a multi-boot test machine using Grub.

Oh my gosh.  :o

It seems that different distros viewed the hard drives and partitions different ways and what was sda on one distro would be sdc on another depending upon which distro was installed on what hard drive.

The whole thing was a nightmare.

I am going to just partition all those drives and use Virtualbox in the "parent" distro to make it all happen.  There is not enough time in life to fight battles that I don't need to deal with.

---

### Post by Giant Speck on 2009-03-14
There is one thing I agree with in the article, and that's the excerpt about GRUB:

> Having the boot manager overwritten by a Windows upgrade is another common complaint. A feature to reinstate the boot manager from the install disk menu would help people who can no longer boot Ubuntu.I recently installed WIndows 7 build 7000 on a 30 GB partition and it wiped out GRUB, causing me to have to reinstall it from an Ubuntu Live CD.  I had never done it before, and it was pretty complicated.

Though, it shouldn't be just Linux developers who should be working to fix this problem.  A third-party application for Windows that can reinstall GRUB would be nice, too, *especially* if the main reason GRUB is not working is because you installed or upgraded to a newer version of Windows.

----------

Now here is something in the article I don't exactly agree with:

> Ubuntu's package management implementation constitutes a significant enticement for the potential switcher in its own right. However, building packages from source is unavoidable when a desired package isn't in the repositories or the version in the repositories is out of date.When I want to install a program that isn't in the repositories, the first thing I look for is a .deb file.  Usually, I'll look on either the developer's website or on GetDeb.  If I cannot find a .deb file, I'll look for an unofficial PPA.  If that doesn't work, *then *I look for the source to compile from.

Though, I will agree that all of these methods of installing a program seem complicated and unnecessary, but I don't think we should dumb down the flexibility of installing applications just because it can seem daunting and complicated to new users.

---

### Post by Bölvaður on 2009-03-14
> **pbpersson said:**
> 
It seems that different distros viewed the hard drives and partitions different ways....


you do realize it doesnt matter what way you identify them, its just grub, has nothing to do with the distro how the partitions are detected... use the way you are comfortable with.

---

### Post by billgoldberg on 2009-03-14
**Screen setup**

Non-issue, always worked fine.

**Boot management**

Never had any serious trouble with it.

I keep a copy of Super Grub Disk at hand, both only needed it a few time (after installing Windows).

**Mounting**

Non-issue.

I don't need it, and if I need it I can get it to works in a minute.

A GUI could be nice, sure.

**Installation**

Never had any problems with apt-get.

**Sound configuration**

ALSA

**Networking: IPv6 support**

This was an issue for me in Ubuntu 7.04, since then I never experienced it again.

**Power and hibernation**

Don't need it.

Even on my netbook I don't use hibernation. 

It's always plugged into the wall.

**Email migration**

Non-issue.

**Documentation**

I think the amount of information on Ubuntu on the Internet is freaking amazing.

When I have Windows issue (not much as I hardly use it), googling for anwsers and actually find something useful the first half hour is rare.

With Ubuntu it takes 10 second, you copy paste 3 commands and the problem is done.

I must say that the new documentation in Windows 7 is pretty awesome.

It gives you the solution.

After a BSOD on Windows 7 beta, a screen popped up, telling me to open the CMD as admin (root), and give a 4 or 5 commands I had to enter.

Now I had the same BSOD a week later, so whatever I did didn't work, but the concept is pretty good.

[B]
Building from source[/B]

Nowadays so many people provide a repository or a deb package that building from source isn't anything I've done for a long time on Ubuntu.


--

I know some people will have other experiences.

---

### Post by Giant Speck on 2009-03-14
> **billgoldberg said:**
> I know some people will have other experiences.

You saved your butt with that comment!

:lolflag:

---

### Post by xpod on 2009-03-14
The only time *i`ve* ever had to mess around with screen settings was back when i had to use S-video to Scart for TV-out on older model TV`s we had at the time.Not a problem now with VGA or DVI/HDMI leads on the new TV`s around the house.
At the moment i also have 2 different size monitors(19" & 22") on my PC and both of them are detected just fine.

We`ve never had a problem booting anything since those first tentative weeks with Ubuntu,when the odd grub** error did happen.Apart from that though Ubuntu has always booted just fine for us.
Similar story for me with the many installations on the many different machines along the way.

I never have a problem now with mounting as any disks or partitions i have are easily accessed via the Places menu & a password and any portable drive or card i ever plug in pops up regardless.

Sound too has always worked great for us.We actually get sound from more than one app at the same time without doing a thing.
Networking has always been fine here too and *i* dont really give two hoots about the power & hibernation thing or indeed the email migration.

Documentation in one form or another is incredibly good(once you know how to find it) and the only thing *i`ve* ever* had* to build from source were some eyetoy drivers.

---

### Post by tsali on 2009-03-14
I have experienced all of the issues that were pointed out in the article...I agree with him completely.

I'm only running about 50/50 on proper video, sound and wireless detection.

Additionally, if a users buys a different monitor at Walmart than what was connected when Ubuntu was installed, it's a pain to setup.

---

### Post by lisati on 2009-03-14
Most of the hassles I had when I first used Ubuntu (7.04) were easily fixed by spending some time on the forums, what few remained are largely non-issues. Some seem to have been addressed when 8.10 but things have gotten sluggish - I suppose I better invest in some extra ram for my Ubuntu machine......

---

### Post by Dr. C on 2009-03-15
**Screen setup**
This used to be an issue with earlier versions of Ubuntu, but with 8.10 the video issue is with a 24in monitor and Nvidia drivers. The problem, incorrect detection of the monitor resulting in an over-scan of the display,is caused by the DRM in the propriety Nvidia drivers and occurs in Vista, Windows 7 and also in Ubuntu 8.10. It can be fixed by editing xorg.conf in Ubuntu or the Windows registry in Vista / Windows 7. The long term solution in Ubuntu is 3D FLOSS drivers for Nvidia which is progressing well through the nouveau project.

**Boot management**
Have not had an issue with this

**Mounting**
Wrong permissions can be fixed by running nautilus as sudo, ```
gksudo nautilus
``` but be warned this can be very dangerous if one does not know what one is doing. Have not had an issue with this.

**Installation**
Have not had an issue with this ever.

**Sound configuration**
Canonical is on the right track with this some short term pain for long term gain.

**Networking: IPv6 support**
Have not had an issue with this, but there is nothing wrong with the suggestion

**Power and hibernation**
This is an area that still needs some work, but Ubuntu has come a long way from say 6.06 to 8.10

**Email migration**
The real issue here is vendor lockin by Microsoft. To migrate email from Outlook Express to an email client on Ubuntu one must first migrate to Thunderbird on Windows to get the emails and contact information etc., out of the locked in propriety Microsoft format, only then can it be migrated to Ubuntu. More better documentation may be the answer here. Is a migration tool even possible here?

**Documentation**
While Ubuntu has very good documentation both in the official and community documentation, there is always room for improvement. This is especially the case when something used to work and no longer works. A good example of this is floppy drive support from 8.04 to 8.10. There are many valid reasons to not include floppy support by default, why load a floppy module on computers that no longer have floppy drives? But documenting how to enable floppy support is important since there are many of us who still use floppies. By the way optical media such as CD, DVD and yes even Blu-ray, are fast becoming obsolete to flash memory, USB keys etc., in some ways even faster than the venerable floppy.  

**Building from source**
There is a very valid point here. Why not include all the packages needed to compile a wireless / wired / modem driver in the default install? This can be valuable when a user who cannot connect to the Internet  because of a missing  driver can obtain the needed driver source code on a CD, USB key etc but still cannot compile the driver because they need to download additional packages. What will happen if Ubuntu started to become really popular and manufactures start including the source code for their drivers, as every FLOSS fan would want and it still does not work?

---

