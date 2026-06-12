---
title: "Where can I find outdated linux isos to download?"
date: 2009-04-30
forum: The Cafe
---

### Post by translucent juicebox on 2009-04-30
There's a program I want to run,  but it's so old that I can't run it in ubuntu, because the kernel and dependencies are too new and incompatible.  More specifically, I'm looking for a small distro with kernel 2.2.x and glib 2.1, preferably DeLi 0.6.1.  I've been looking around on distrowatch, and it seems like most distros don't host .iso files for older versions.

Could someone point me in the direction to a website that hosts older linux isos?


Sorry if this is a bad place to post, I couldn't find a technical help subforum dedicated to OS's other than ubuntu.

---

### Post by fjf on 2009-05-01
Dont know if this helps, but you can take a look here:  [ftp://ftp.rediris.es/pub/linux/distributions/](ftp://ftp.rediris.es/pub/linux/distributions/)

Or here:

[http://ibiblio.org/pub/historic-linux/distributions/](http://ibiblio.org/pub/historic-linux/distributions/)

---

### Post by skymera on 2009-05-01
Here:

[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by disturbed1 on 2009-05-01
> **translucent juicebox said:**
> There's a program I want to run,  but it's so old that I can't run it in ubuntu, because the kernel and dependencies are too new and incompatible.  More specifically, I'm looking for a small distro with kernel 2.2.x and glib 2.1, preferably DeLi 0.6.1.  I've been looking around on distrowatch, and it seems like most distros don't host .iso files for older versions.

Could someone point me in the direction to a website that hosts older linux isos?


Sorry if this is a bad place to post, I couldn't find a technical help subforum dedicated to OS's other than ubuntu.

What is the program's name?

You do know, that if you were to locate something a kernel that old, it most likely would not run on anything made in the last 7-10 years ;) Your best shot would be to use qemu.

glibc 2.1 is also quite old. Deli is a special linux distro made for old PCs, based on Slackware. Unfortunately I could not locate a mirror for Deli.

The oldest distros I quickly came across where Slackware 8.1 (ftp download only) with glibc 2.2, and Vector Linux also 2.2. You can get Vector's ISO images at any of their mirrors.

Ubuntu has only been out for a couple of years. The oldest version (Warty) still has a 2.6 Kernel, and far too new of a glibc to be compatible with a binary compiled for glibc 2.1.

You could attempt to install glibc 2.1 along your current glibc. Export the correct flags before running your program. Do this on a test machine, or inside a VM. You do not want to mess up the current glibc. In the long run, it would honestly be better to just compile a new version of that program for a modern system. Or find an alternate program.

I'm still intrigued as to which program you have? I remember some of the older Loki installers required ancient glibc versions. Most of these where patched to work on newer systems before they went out of business.

---

### Post by translucent juicebox on 2009-05-01
yup, 10 years is about how old of a distro I need.  I'm trying to install Simcity 3000(the linux version), and figuring out the dependencies problems with ubuntu 8.10 is just too confusing, so my plan is to find an old OS that simcity 3000 will be compatible with and run that OS inside of virtualbox, and then playing it in that to avoid conflicting dependencies with ubuntu 8.10.

I'm downloading slackware 8.1 right now, hopefully this'll work.

Also, I thought the game could only be patched after installation.  Is it possible to patch the installation iso?

---

### Post by disturbed1 on 2009-05-02
:) 

It's a Loki installer.
Try this.
[http://www.gentoo-wiki.info/HOWTO_Running_Old_Loki_Games#Sim_City_3000](http://www.gentoo-wiki.info/HOWTO_Running_Old_Loki_Games#Sim_City_3000)

---

