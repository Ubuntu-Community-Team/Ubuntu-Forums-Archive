---
title: "Virtualbox connection instability, software download problems"
date: 2009-12-12
forum: Virtualisation
---

### Post by slowtrain on 2009-12-12
I just installed Ubuntu 9.04 Jaunty in VirtualBox on a Windows laptop (the laptop is from work--I'm normally 100% linux).  

I've run into some headaches though and am wondering if these are known problems with any workarounds.

First, my internet connection is quite unstable from Ubuntu, but apparently not from Windows.  A couple examples:  Skypes is so garbled on Ubuntu I can't use it (especially uploading my voice), but Skypes on Windows works fine.  ssh connections get disconnected every few minutes (will try ssh from windows next....).

Second, I can't seem to make certain software downloads work.  For example, I put medibuntu in my software sources, reload, but can't see Skype (is there a Medibuntu version of Skype for 9.04?).  Also checked & can't see anything called libdvdcss.  Also, in R, I tried to install JGR using install.packages, but no matter which mirror I went to, it kept telling me that JGR is not available.

Anyone have any clues on what's happening w/ this?

---

### Post by lmarmisa on 2009-12-12
In relation with the inestability of your internet connection, try to switch from NAT to Bridge mode in your VM network interface. It works fine, but probably your LAN has to support DCHP because a new LAN IP address has to be negociated (no negotiation is needed with NAT).

I don't know if your computer is powerful enough for running heavy programs with strict requeriments about real time in your VM. Check also if the memory of your VM for Ubuntu is too low o high. I feel confortable with memory sizes from 350 to 500 Mbytes.

---

### Post by slowtrain on 2009-12-13
Thanks lmarmisa!  The suggestion of switching from NAT to bridging seems to have worked (I also made a couple other setup changes, including allowing nested paging and direct physical address access, but I doubt these would so greatly affect my internet connections).  My ssh connections are now stable and Skype isn't nearly as garbled.

I wonder why VB uses NAT as the default if it is such a liability.  Maybe the DHCP thing, though I imagine most people have DHCP these days.

You are also right to have some concern for my processor speed.  I'm on a fast Core 2 Duo laptop, but I installed a 64-bit version of Linux on a 32-bit windows system; with this setup VirtualBox cannot access both processors, just one.  Yesterday I was hitting some pretty high loads, though this also seems better today.  People installing Ubuntu in VB should keep this in mind--wish I had just installed the 32 bit version.

---

