---
title: "What other distros should I try?"
date: 2019-06-15
forum: Ubuntu, Linux and OS Chat
---

### Post by kpatz on 2019-06-15
I'm trying to get more well rounded in different variations of Linux, especially in terms of installation, administration, setup, updates, package management/software installation, security etc.

I've used Ubuntu for years and am (mostly) comfortable with how things work and how to fix or tweak them.  I recently installed Centos 7 in a VM and have been learning that ecosystem and am slowly getting more familiar with it as well.  A lot of things are done differently in Centos/Redhat/Fedora than in Ubuntu/Debian.

I've also played with Linux Mint in the past, but that's mainly just Ubuntu with a different face... a different desktop manager.

So, in interest of educating myself, what other distros should I try, that are different from Ubuntu?  Arch? SUSE? 

I suppose in addition to this, I should play around with more desktop environments like KDE, MATE, etc.  I've messed with xfce some (Xubuntu and Mythbuntu).

Suggestions y'all?

---

### Post by cruzer001 on 2019-06-15
Maybe you should consider rolling your own.  I'm working on a new project, guess you could call it a micro build.
> terminator terminal emulator
pico or nano text editor
links2 or browsh browser
midnight-commander file manager
xdm display manager
xmonad window manager
xserver.xorg
That should be the complete OS.

For my daily system I started with gnome-core package and built on that.  Gnome-core is well put together and easy to add to.

Anyhow, just a thought

---

### Post by Rubi1200 on 2019-06-15
I've recently been testing MX Linux (based on Debian stable) and ArcoLinux (based on Arch). 

Am impressed with some of the interesting features that both have to offer.

Would recommend taking them for a spin, so to speak.

---

### Post by kpatz on 2019-06-15
> **cruzer001 said:**
> Maybe you should consider rolling your own.  I'm working on a new project, guess you could call it a micro build...What distro are you installing that has "nothing" included to start with?  Some sort of minimal Ubuntu install?

I suppose if I really wanted to roll my own, I would start from the kernel up... LOL.  Now that would be a project.

I'm mainly wanting to learn the package and administration management of various distro groups... I already know Debian's apt, and am getting familar with Centos/RHEL/Fedora's yum.

P.S. I use terminator too. :)

---

### Post by cruzer001 on 2019-06-15
Yes you can start with just the kernel, but when your finished you will probably find it has the same content as the prebuilt packages already offered for such builds.

I rarely distro hop, but Solaris stood out for me.  Been around for 20+ years.  Oracle took it over 9 years ago and is now called Oracle Solaris.

---

### Post by Dennis N on 2019-06-15
Try Manjaro using the Manjaro Architect installer. With that, you can install any desktop environment they offer, with a full desktop install or minimal install. Options to pick the kernel to use, boot loader, applications and so on.

---

### Post by TheFu on 2019-06-15
Gentoo if you really want to be forced to learn Linux.  Then use Linux from Scratch to make your own distro.

TinyCore if you need a 12MB Desktop. Great for highly specialized needs.

Slackware if you want some history.

Arch if you think slackware is too hard, but still want the pain.

Alpine of you do virtual machines or containers and *lite* is desired.

CentOS v8 - Join everyone in pain.

---

### Post by kpatz on 2019-06-15
> **TheFu said:**
> CentOS v8 - Join everyone in pain.Centos 8 isn't even out yet, is it?  Or is it in development/pre-release like Ubuntu 19.10?

---

### Post by ajgreeny on 2019-06-15
I would also suggest Arcolinux, a simpler to install version of Arch, as worth trying. It's a rolling release so once installed you have only to keep running normal updates and never (in theory, at least) install again.
It is not so simple to use (in my opinion), particularly for installation of some packages that are very much run of the mill for me in Xubuntu, such as Libreoffice, surprisingly.  That may.however, be simply because I am now so familiar with the Ubuntu family of OSs that I have not had any big problems or difficulties for a very long time

I tried it in a dual boot with Xubuntu-18.04 on my laptop recently and it worked extremely well for a fair time, but then I completely broke the boot system by deleting an incorrect entry in the /boot/efi partition; using Boot-repair did not help, unfortunately so I got rid of both the Xubuntu and Arcolinux and reinstalled Xubuntu with which I'm more comfortable after nearly 15 years of a *Ubuntu system.

If I had more time to investigate I would certainly investigate Arcolinux again, but as a single install next time.

---

### Post by tea for one on 2019-06-16
If you are attracted to build your own system but starting from a position where all the nuts and bolts (e.g. network, graphics, sound) are already installed, then:-

[https://unit193.net/xubuntu/](https://unit193.net/xubuntu/)

Also, I agree with the suggestion in post 3 about MX Linux. It has an interesting collection of MX Tools, especially the Remaster utility.
In essence, you boot up a live session, add and remove packages as you wish, then create a new bootable iso (including persistence if required). 

I found it to be quite entertaining.

---

### Post by kc1di on 2019-06-16
As has been pointed out already Manjaro/Arch and Gentoo distrobutions should be added to your list.  There are four basic bases of linux distributions. Debian upon which Ubuntu/Mint/MX are base on RPM upon which Redhat/Fedora/Suse/Cent are based upon, Arch/Manjaro  and Gentoo.  All others are basically derivatives of those four groups. You should try OpenSuse because of Yast and familiarize yourself with how it works also.  Good luck.

---

### Post by Artim on 2019-06-16
Wanna try an ultra-stable, historic Linux distro that is still usable by ordinary humans?  Try Slackware-based **Salix OS!**  A nice Xfce desktop (feels like Xubuntu) and ultra-super-mega stable.  What Ubuntu did for Debian - making it easier for us non-geeky "ordinary mortal" desktop users, Salix OS has done for Slackware!  Just try the Live stuff before you try installing it... it's not nearly as easy to install as the 'buntu family.

**MX-Linux** is soaring to the top of Distrowatch, and for good reason!  The heir of Mepis, with cool stuff from antiX, MX is based on Debian Stable and sports a highly sperecialized (but still simple and infinitely configurable) Xfce desktop.

Want super speed?  Try antiX and **Bunsen Labs**.

---

### Post by xavierbaez on 2019-06-16
You should try Red Hat 8.

It is one of the first distributions plus you can get a job on IT as a Cloud Administrator if you are really good with CentOS 7 and Red Hat. 
The new Red Hat 8 gives you opportunity to learn what's new, it will help your career.

---

### Post by charlieg on 2019-06-19
Shout out for Bodhi Linux, with its Moshka desktop (a fork of e17).

[https://www.bodhilinux.com/](https://www.bodhilinux.com/)

---

### Post by Rubi1200 on 2019-06-19
> **charlieg said:**
> Shout out for Bodhi Linux, with its Moshka desktop (a fork of e17).

[https://www.bodhilinux.com/](https://www.bodhilinux.com/)

Yes, agree.

Lots to like about Bodhi though I have not used it for some time now.

---

### Post by hk42 on 2019-07-13
Debian is used in lots of non Intel devices.
So I think getting used to it is not a bad idea.

---

### Post by lammert-nijhof on 2019-07-13
Distro hopping a completely useless hobby, equal to self-satisfaction. Just do some something useful install Ubuntu on zfs and improve your response times. Separate your work over 2-4 different containers or VMs to improve performance and security. Use a freenas server.

---

