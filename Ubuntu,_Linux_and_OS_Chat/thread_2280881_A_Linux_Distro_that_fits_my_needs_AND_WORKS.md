---
title: "A Linux Distro that fits my needs AND WORKS"
date: 2015-06-03
forum: Ubuntu, Linux and OS Chat
---

### Post by bluesoviet on 2015-06-03
Hello Ubuntu community, it's been awhile hasn't it? Not that any of you would remember me since I've only really posted in the support section a few times before giving up on Linux for awhile... yeah...

But with the Windows 10 Insider preview coming to a close, I want to put a Linux Distro on my second HDD again. Problem is, I can't find one that fits my needs AND WORKS that I haven't already tried. Can anyone lend a hand in helping me find one?

What  I need:
-Up-to-date graphics drivers(Proprietary only, NVIDIA 750 TI)
-Gnome 3.14 or newer(preferably, really want 3.16)
-Steam support
-Decent default apps(for example, LibreOffice)
-Firefox or Chromium web browser
-WORKS

Distros I've tried:
Ubuntu 14.04
Ubuntu Gnome 14.04
Ubuntu Gnome 15.04
Debian 7.8(I think?)
Fedora 21
SteamOS "Alchemist"

---

### Post by buzzingrobot on 2015-06-03
1. I have a 750ti. If you want to use an Nvidia proprietary driver, you will need a recent kernel and one of the 346 drivers from Nvidia. To use the open source Nouveau driver, I've found that the 3.19 series kernels used in 15.04 are needed. (Due, I think, to lack of info from Nvidia re: the Kepler cards.)

2. Ubuntu Gnome 15.04 ships with 3.14.  You can install 3.16 from that spin's PPA's, but many of the packages will not be release-ready. Blogs and websites that offer cut-and-paste instructions for upgrading to 3.16 often don't mention that.  You should visit each PPA page on Launchpad and read any cautions and advice posted there before using them. At present, Arch (and some of its derivatives) and Fedora 22 are probably the best places to turn for Gnome 16. Gnome's release cycle and Ubuntu's release cycle are out of sync:  Ubuntu releases one month after Gnome.

I don't use Steam. but I know it's used in Ubuntu and Fedora and, I assume Arch.

Firefox is universally available. Chromium is usually available if someone packages it for a distro.  Chrome, of course, is packaged and distributed by Google for Debian, Ubuntu, Fedora and OpenSuse.

If Gnome 3.16 is not a must have, I'd look at Ubuntu 15.04.  If Gnome 3.16 actually is a must, I'd look at Fedora 22. But, remember that Fedora does not (cannot) ship with multimedia codecs or Flash or the adustments to freetype/fontconfig that Ubuntu uses to improve font rendering. Nor does it provide packages like ubuntu-restricted-extras that allow users to install those things post-installation. Third-party repos can be enabled to provide those things.  So, if you consider Fedora, I'd do a bit of research first. (Note that while many, like me, find Fedora is a fine daily desktop, it is a fast-moving distribution that debuts much new technology. Updates are numerous and frequent.)

If you choose Ubuntu 15.04, use the "Additional Drivers" tool to install the Nvidia proprietary tool.  Pick the recommended "tested" driver.  

Note that 15.04's lifetime is 9 months.  Fedora 22's is effectively 13 months (was released last week).

"WORKS" is always dependent on what we want the thing to do. On *any* distribution, Steam is an independent third-party addon that follows its own development cycle. What does that mean?  It means that if the version of Steam (or something else you have installed) requires a certain Nvidia driver release and you upgrade to a newer release that is not supported, then you'll need to wait for Steam to fix things and release its own upgrade that can use the new driver (or downgrade back to the driver it can use).

---

### Post by monkeybrain20122 on 2015-06-03
> **buzzingrobot said:**
> 
But, remember that Fedora does not (cannot) ship with multimedia codecs or Flash or the adustments to freetype/fontconfig that Ubuntu uses to improve font rendering. Nor does it provide packages like ubuntu-restricted-extras that allow users to install those things post-installation. Third-party repos can be enabled to provide those things.
.

All those things can be installed by adding the rpmfusion repos (free and non free), they are kind of like Debian media or the now defunct Medibuntu ppa. Except for libdvdcss which even rpmfusion would not host. But you can either get it from videolan or the livna repo.

In general though, I think there are a lot more precompiled packages for Ubuntu, whether from official repos or ppas.

---

### Post by buzzingrobot on 2015-06-03
> **monkeybrain20122 said:**
> All those things can be installed by adding the rpmfusion repos (free and non free), they are kind of like Debian media or the now defunct Medibuntu ppa.

Yes, of course, it's the "third-party" repo. The OP will need to research what, specifically, to add, though, since rpmfusion doesn't offer any handy bundles. (There are some guides at the Fedora forums.)  Other post-install scripts, like Fedy, are out there, but there can be issues pop up with them -- like installing repos they don't tell you about or pulling in large numbers of dependencies (I once saw one of them silently install almost all of the KDE packages as dependencies for *one* package.)

---

### Post by monkeybrain20122 on 2015-06-03
> **buzzingrobot said:**
> Yes, of course, it's the "third-party" repo. The OP will need to research what, specifically, to add, though, since rpmfusion doesn't offer any handy bundles. (There are some guides at the Fedora forums.)  Other post-install scripts, like Fedy, are out there, but there can be issues pop up with them -- like installing repos they don't tell you about or pulling in large numbers of dependencies (I once saw one of them silently install almost all of the KDE packages as dependencies for *one* package.)

No, I wouldn't use any post install script if I don't know what it does.

---

### Post by bluesoviet on 2015-06-03
Thanks, i'll try Fedora 22. But does it come with the proprietary drivers? If not, can you link a guide on doing so?

---

### Post by buzzingrobot on 2015-06-03
> **bluesoviet said:**
> Thanks, i'll try Fedora 22. But does it come with the proprietary drivers? If not, can you link a guide on doing so?

No proprietary drivers or code. The primary source for these is [http://rpmfusion.org/](http://rpmfusion.org/), a volunteer community effort. Instructions for installing the RPMFusion repos are on that page (there are two: free and non-free) and the needed RPM's are linked there.

Guidance on installing Nvidia's drivers from RPMFusion are here: [http://rpmfusion.org/Howto/nVidia?highlight=%28CategoryHowto%29](http://rpmfusion.org/Howto/nVidia?highlight=%28CategoryHowto%29).  Be sure to read everything there, first.  I've had good luck with it, but using Nvidia's (or AMD's) drivers obviously still causes problems for many.  As I mentioned, Fedora upgrades frequently, including kernels. Don't be surprised to see a couple hundred updates immediately after installing Fedora 22 (and you should do those updates.)

If an Nvidia card is active during the install, the Nouveau driver will be used. 

Speaking of updates, Fedora Gnome defaults to automatic updates.  You'll see an alert in Gnome asking you to reboot to install them.

The codecs and such you will likely want from rpmfusion are tallied here: [http://www.mjmwired.net/resources/mjm-fedora-f19.html](http://www.mjmwired.net/resources/mjm-fedora-f19.html). Although it's 2 years old, the package names haven't changed and the guidance is still good. You'll see 'yum' mentioned, which was the command line package manager front end for Fedora (like apt-get in Ubuntu/Debian).  Yum is replaced in F22 by 'dnf' -- same command structure, different internals.

The GUI software app is called just "Software".  You can also do updates with it.  It's an application-centric program and usually won't show you a fine-grained view of repos that includes everything.  For that, install "yumex-dnf", a bit of a work-in-progress, but useful. (I suggest using its search mechanism after rpmfusion is enabled to find and install those codecs.)

Fedora wants you to use this page to download iso's: [https://getfedora.org/](https://getfedora.org/). 'Fedora Workstation' is Gnome 3.16.2, and 'Fedora Spins' include KDE, XFCE, LXDE, and Mate/Compiz.

Fedora docs: [https://docs.fedoraproject.org/en-US/index.html](https://docs.fedoraproject.org/en-US/index.html).

---

### Post by bluesoviet on 2015-06-03
Thanks for the info. however, Fedora 22 just won't boot to the live image for me to install(via UEFI). It gets to the very last bit of the circle, hangs for a bit, and then tells me its missing two files and forces me into a "emergency" command line interface. All I did was copy the files to a USB drive, does that not work for Fedora 22?

Edit: You say that Fedora doesn't offer the proprietary drivers, correct? Don't the open-source drivers perform worse than the proprietary drivers?

---

### Post by buzzingrobot on 2015-06-03
You can't copy the image.  You need to "burn" the image to a USB stick or a DVD. It's a byte-for-byte transfer, not a file copy.

Fedora has some instructions here: [https://docs.fedoraproject.org/en-US/Fedora/22/html/Installation_Guide/sect-preparing-boot-media.html](https://docs.fedoraproject.org/en-US/Fedora/22/html/Installation_Guide/sect-preparing-boot-media.html).  There are also howto's somewhere at ubuntu.com's download section.

I generally use the 'dd' method, as shown at the Fedora doc link. I do add a "sync" to it to make sure everything flushes out of RAM onto the stick:

> sudo dd if=*/path/to/Fedora-Live-Security-x86_64-21.iso* of=*/dev/sdd && sync;*

Like they say, be sure you correctly designate the destination disk.  This wipes out everything on the destination disk and replaces it with the install iso.

The 'sudo' is there because you need to be root. The process will take at least a few minutes, likely several.  The prompt returns when it's completed.

The open source Nouveau driver is fine for Gnome itself and general applications. For demanding games, you probably want the Nvidia driver. My advice would be to avoid installing a proprietary driver until you have the system otherwise setup and configured to your liking.

---

### Post by bluesoviet on 2015-06-04
Not using Linux ATM, I'm currently using Windows 7 so I can't do all the fancy commands. But even when I used the programs listed in the download page and it still didn't work.

<sigh> Whatever, I guess I won't install any Linux distro afterall. I would have thought that things might have gotten at least a little better since I last used Linux but it would appear that its still all broken and useless as I left it.

---

### Post by malspa on 2015-06-04
> **bluesoviet said:**
> it would appear that its still all broken and useless as I left it.

I had a feeling something like this was coming. Interesting that so many other people happily use this "broken and useless" operating system. Lots of us have been running Linux for years and years. Kinda makes you wonder, doesn't it? :)

---

### Post by night_sky2 on 2015-06-04
Xubuntu, Kubuntu, Linux Mint, LXLE.. 

At the end of the day, you would have to try yourself. I remember my days of distro-hopping which was time-consuming but thankfully they are behind me.

 If you are looking for perfection though, I doubt you'll find it. Not even mainstream OSes such as Microsoft or OSX will offer it.

---

### Post by Elfy on 2015-06-04
Closing this now, given that everything is broken and useless there seems little point in keeping it open.

---

