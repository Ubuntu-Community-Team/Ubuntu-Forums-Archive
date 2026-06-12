---
title: "Question about Debian Testing netinstall"
date: 2010-03-09
forum: The Cafe
---

### Post by blueshiftoverwatch on 2010-03-09
Is there any difference between installing Debian Testing from the netinstall CD versus the regular method?

My theory was that I'd just download the netinstall so that I'd automatically get all of the most recent software included in Testing and not have to spend any time installing updates once the OS is installed.

Will the netinstall CD just install a basic Linux OS and have me use the prompt where I'll have to manually apt-get install the packages I want? Or will it provide me with a template (kind of like Fedora and Slackware do) where it'll ask me what kind of setup I want to do (desktop, server, workstation, etc), what desktop environment I want (Gnome, KDE, Xfce, Lxde), and so on?

If it does provide with a template, will a desktop netinstall be exactly the same as a desktop install done using the standard method where you install from the CD/DVD's? Only I'll probably have slightly newer software and probably won't have any updates to install once I get the system up and running?

---

### Post by swoll1980 on 2010-03-09
> **blueshiftoverwatch said:**
> Is there any difference between installing Debian Testing from the netinstall CD versus the regular method?

My theory was that I'd just download the netinstall so that I'd automatically get all of the most recent software included in Testing and not have to spend any time installing updates once the OS is installed.

Will the netinstall CD just install a basic Linux OS and have me use the prompt where I'll have to manually apt-get install the packages I want? Or will it provide me with a template (kind of like Fedora and Slackware do) where it'll ask me what kind of setup I want to do (desktop, server, workstation, etc), what desktop environment I want (Gnome, KDE, Xfce, Lxde), and so on?

If it does provide with a template, will a desktop netinstall be exactly the same as a desktop install done using the standard method where you install from the CD/DVD's? Only I'll probably have slightly newer software and probably won't have any updates to install once I get the system up and running?

If I remember right, it has a method like freeBsd where you select packages by hitting the space bar in the little squares next to the package. If you've done a freeBSD install you will know what I'm talking about.

---

### Post by cascade9 on 2010-03-09
I cant recall with the netinstall version, but I do know that testing full CD/DVD has a different .iso for the KDE and Xfce/Lxde version. 

IIRC, when I did use netinstall, it was pretty much the same as the full CD version....you didnt boot into a CLI only system and have to manually install a DE/WM. It does ask you what you want to use the system for, but its got different options what you have posted (IIRC, its 'desktop', 'apache', 'mail server' and a few other options)

---

### Post by NightwishFan on 2010-03-09
The packages selection mode is called tasksel. Run it as root, or just use aptitude.

---

### Post by Xbehave on 2010-03-09
> **blueshiftoverwatch said:**
> Is there any difference between installing Debian Testing from the netinstall CD versus the regular method?
Never done a full debian install but the netinstall has no xorg or nice gui (it has a TUI and a basic GUI to guide you through the install).

> My theory was that I'd just download the netinstall so that I'd automatically get all of the most recent software included in Testing and not have to spend any time installing updates once the OS is installed.
This will work more or less, however if you reinstall you will have to download everything again whereas with the normal install you will already have most packages on the CDs you downloaded last time.

> Will the netinstall CD just install a basic Linux OS and have me use the prompt where I'll have to manually apt-get install the packages I want?
You get a basic installer, from the installer you can install various tasks or even select the packages you want. So you can go installer -> GUI, or if you want installer->CLI, reboot into CLI, CLI->GUI

> Or will it provide me with a template (kind of like Fedora and Slackware do) where it'll ask me what kind of setup I want to do (desktop, server, workstation, etc), what desktop environment I want (Gnome, KDE, Xfce, Lxde), and so on?
It will give you choices, one of those choices is pick package manually.

---

### Post by J_Stanton on 2010-03-09
if i recall correctly, debian testing updates its cd .iso's weekly, so if you download it, it will be pretty much up to date.

---

### Post by cascade9 on 2010-03-09
> **J_Stanton said:**
> if i recall correctly, debian testing updates its cd .iso's weekly, so if you download it, it will be pretty much up to date.

Theres 2 versions of the full version of testing- the 'alpha 1' (slightly older) and 'weekly snapshot'- 

[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)

The netinstall version is a daily build "which contain the latest available version of installer components".

---

### Post by blueshiftoverwatch on 2010-03-09
> **cascade9 said:**
> Theres 2 versions of the full version of testing- the 'alpha 1' (slightly older) and 'weekly snapshot'-
Thanks, I somehow completely overlooked that in my rush to download the ISO image. I'm going to download the alpha1 as the whole point in using Testing over Unstable is that your assured more stability.
> **cascade9 said:**
> The netinstall version is a daily build "which contain the latest available version of installer components".
What's the point of having two versions of Testing? If theirs going to be a Testing weekly build why not just install Unstable?

I would have thought that the netinstaller would give the user the option to choose whether he wanted to use the latest weekly build or alpha1.

---

### Post by XubuRoxMySox on 2010-03-10
The latest weekly build is just a "snapshot" of Testing (including whatever security updates have been issued). That's the better choice IMO.

If you want "to boldly go" and take a little risk, have a look at Sidux! Yet even Debian Sid is not the *most* bleeding edge stuff. For that you want Debian *Experimental*. Hahaaa! Be prepared for some surprises and crashes and danger, but enjoy the ride!

Absolutely rock-solid stable: Lenny.

In-between Unstable (meaning un*proven* - not necessarily unstable) and Stable, there is Testing. The weekly snapshot is like getting an up-to-date ISO to start from. 

Debian is every bit as easy to install and use as Ubuntu is, as long as you pay attention to what you are doing and make informed choices along the way.

-Robin

---

### Post by blueshiftoverwatch on 2010-03-10
Why does Debian Testing not include the Testing repos by default in apt-get? You have to add them manually. I find this odd.

---

### Post by blueshiftoverwatch on 2010-03-11
> **blueshiftoverwatch said:**
> Why does Debian Testing not include the Testing repos by default in apt-get? You have to add them manually. I find this odd.
I enabled the Testing repo but when I go to log off I see "Debian Testing/Sid" flash across the screen for some reason. Why would it say Sid (unstable) when I don't have any Unstable repos enabled in apt?

---

### Post by NightwishFan on 2010-03-11
It likely just means either. Probably something to do with the kernel version. My other machine on testing says that as well.

---

