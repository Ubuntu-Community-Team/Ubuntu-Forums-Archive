---
title: "Xubuntu 11.10 - abysmal install failure"
date: 2012-03-10
forum: Testimonials &amp; Experiences
---

### Post by scruffyeagle on 2012-03-10
I have a Toshiba Satellite A205 notebook w/ several partitions. It was set up like this before the attempted Xubuntu installation:
1) 14GB - Kubuntu v10.04 LTS 32-bit
2) 4GB - swap
3) 14GB - Debian Squeeze
4) 14GB - unused Ext4
5) 5GB - FAT
6) 66GB - Ext4

I used #6 as /home for both Kubuntu & Squeeze, w/o any problem or conflict that I could detect.

I downloaded, verified ISO, verified good burn, and then attempted install of Xubuntu v11.10 32-bit into the unused 4th partition. I did the same as w/ the 2 earlier OS's, using partition #6 as /home for Xubuntu. The installation seemed to go without a hitch, but when the system rebooted the Kubuntu partition was listed in the Grub menu as being an MS-DOS installation. So now, the Kubuntu installation is completely inaccessible.

To cap that off, when I tried to boot into the new Xubuntu installation, here's what happened:
*) I got the login screen for Xubuntu.
*) It let me select the username I'd entered during install,
*) it let me type in the password,
*) it would go to terminal mode displaying the startup details,
*) it gets as far as displaying that it's checking the battery state,
*) then it goes back to the login screen.

It does that sequence regardless of whether I select the Xfce session or Xubuntu session. It will allow me to have a "Guest" session - but, what good is that? I need to be able to tweak settings, update, install software, etc.!!!

The "live" session I did before installation seemed really great. I was looking forward to using it. Now, I'm severely disappointed. I'd checked out Unity last week; i.e., Ubuntu v11.10 - and it was crap. The WORST, most useless desktop interface I've ever seen in 30 years of computing. I'm tempted to just wipe the Xubuntu I installed tonight, reinstall the Kubuntu, and then abandon any attempts at using Xubuntu OR any v11(12?).xx variants of Ubuntu, and stick w/ the v10.04 LTS. Period.

---

### Post by sudodus on 2012-03-10
If your hardware is good enough for Kubuntu, stick with it and enjoy :-)

Honestly, I think 12.04 LTS 'precise' will be much better than 11.10 in general. I have recently downloaded the daily build (now at beta stage) of 12.04 Lubuntu, and it makes old hardware fly. Anyway, it might be a good idea to continue with Kubuntu 10.04 and wait until July to upgrade to Kubuntu 12.04. In the meantime you can try various flavours of 12.04 live.

---

### Post by sudodus on 2012-03-10
More thoughts...

Maybe xfce has problems using the same /home partition.

And instead of reinstalling Kubuntu, you should be able to reinstall grub to point to the Kubuntu partition. Try the tips in the following link
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1195275_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275")

look for [COLOR="RoyalBlue"]Reinstalling GRUB 2 from LiveCD[/COLOR]

---

### Post by Cæncel on 2012-03-10
okay, first i'm too Xubuntu user since the tragedy of Unity/Gnome3 Desktop, it works like a charm so no blame on the instalation from the CD, i say yours is more likely a human error

It's sounds to me that you are trying to start a session with something is not there and the problem may be that you don't have a clean "/home" directory, so something is setup to load at the start of your session and fails miserably, it can be anything so you can do two things:

1.- Login via terminal (with f8 or f7, can't remember) and do a "sudo apt-get install kubuntu-desktop" so you can start with a Kubuntu session and then log out properly to start a Xubuntu session

if that doesn't help try

2.- Via LiveCD browse your "/home" partition/directory and look for configuration files, example, the folder ".config" and rename it/delete it, in theory this will give you a clean home directory allowing Xubuntu to create new ones, but be aware that you may lose the settings from past configurations, also you don't need to delete folders named after software likes ".amsn" ".purple" and so. use this one as a last resort and always prefer rename over deleting anything unless you find it disposable

---

### Post by scruffyeagle on 2012-03-12
> **sudodus said:**
> More thoughts...

Maybe xfce has problems using the same /home partition.

And instead of reinstalling Kubuntu, you should be able to reinstall grub to point to the Kubuntu partition. Try the tips in the following link
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1195275_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275")

look for [COLOR="RoyalBlue"]Reinstalling GRUB 2 from LiveCD[/COLOR]

Thanks, sudodus. I'll go read up, in the hopes of avoiding a full reinstallation of Kubuntu. Anyway, knowing how to reinstall Grub is kind of a basic Linux skill, isn't it? I think I should just approach this as an overdue learning task, and try to master it.

---

### Post by scruffyeagle on 2012-03-12
> **Cæncel said:**
> okay, first i'm too Xubuntu user since the tragedy of Unity/Gnome3 Desktop, it works like a charm so no blame on the instalation from the CD, i say yours is more likely a human error

It's sounds to me that you are trying to start a session with something is not there and the problem may be that you don't have a clean "/home" directory, so something is setup to load at the start of your session and fails miserably, it can be anything so you can do two things:

1.- Login via terminal (with f8 or f7, can't remember) and do a "sudo apt-get install kubuntu-desktop" so you can start with a Kubuntu session and then log out properly to start a Xubuntu session

if that doesn't help try

2.- Via LiveCD browse your "/home" partition/directory and look for configuration files, example, the folder ".config" and rename it/delete it, in theory this will give you a clean home directory allowing Xubuntu to create new ones, but be aware that you may lose the settings from past configurations, also you don't need to delete folders named after software likes ".amsn" ".purple" and so. use this one as a last resort and always prefer rename over deleting anything unless you find it disposable


Thanks, Caencel. I can see how a home directory configurations file conflict might be the problem. The machine I'm doing all this on is my spare machine, not my primary. I just use Ubuntu v10.04LTS 32-bit on my primary. It works well, so I don't mess with it; i.e., "If it ain't broke, then don't fix it!". I've had the Toshiba notebook taking up space on my shelf for about a month since my mother gave it back to me. (She just couldn't adjust to switching from Windows.) About a week ago, I decided to make it my project machine, and experiment with other variants of Linux. So far, 2 successes & 1 abysmal failure.

You know, I NEVER use the stock folders OS's set up as "home" directories for my normal workflow. Their existence is a Windows thing, for dummies who can't understand filing systems. I never use them, because I figure if someone manages to hack in, invading directories with those names will be some of the first queries they send. It won't stop them, but it might slow them down long enough for me to figure out I've been hacked and pull the plug. So, I'm thinking that letting the OS's set up their stock "home" folders in the same partition as the system files isn't such a big risk after all, and being basicly empty they'll never take up much space, so I should do that instead of setting a separate partition as "home". The question is, will the installers let me use the same partition as / & home, when I'm doing a custom install specifying which (& only one) partition for installation to?

That's a good suggestion, re. terminal install of Kubuntu desktop. I'll probably try it.

Here's something I've been wondering about... Is it possible to redefine where the home directories should be stored, AFTER the installation has finished? In other words, to relocate them? If it is possible, then before installing the Kubuntu desktop to the Xubuntu partition, I should move both the Kubuntu's & the Debian Squeeze's home directories out of that 6th partition and into the partitions occupied by their respective OS's. Whaddya think?

---

### Post by Elfy on 2012-03-13
> Here is your opportunity to tell other forum members about your experience of Ubuntu. Please do not use this section for support questions, bug reports, or debate. 

Closed.

---

