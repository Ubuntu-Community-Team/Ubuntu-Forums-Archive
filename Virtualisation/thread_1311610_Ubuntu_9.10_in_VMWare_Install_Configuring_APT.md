---
title: "Ubuntu 9.10 in VMWare Install Configuring APT"
date: 2009-11-02
forum: Virtualisation
---

### Post by RealG187 on 2009-11-02
At school the computers are running Windows 7 and if we need to use other OSes (Like XP for the XP course, Server 2003 for the Server Course, Fedora and/or Ubuntu for the Linux course) we use VMWare.

I am trying to install Ubuntu 9.10 in VMWare server and it's stuck at 80% on "Configuring APT"

Should I click skip, what are the consequences of doing so?

Update: I skipped configuring APT and the VM just gave a black screen when booted :(
I also forgot to mention this is Windows 7 64 Bit and I am using VMWare 32 bit running 32 bit Ubuntu if that matters...
EDIT2: When I try to boot 9.10 64 bit it gives an error that an 1686 CPU was detected. Does 32 bit VM Ware emulate a 32 bit CPU only? 64 Bit Ubuntu was in the list of operating systems...


======================
EDIT: Fixed the installation being stuck at "Configuring APT" turns out Ubuntu was trying to connect to the repositories to update the package lists and stuff and the school's internet is really slow, so I disconnected the virtual network adapter and as soon as I did that the installation continued like normal!

---

### Post by fjgaude on 2009-11-02
I would think your base computer should be running 64-bit to run a 64-bit guest...

---

### Post by RealG187 on 2009-11-02
It's Windows 7 64 bit, but VM Ware is 32...

---

### Post by mgrosvenor on 2010-02-26
I have also had this problem. I'm running VMware fusion on an on a Mac. I have a feeling this has nothing to do with the word size (32bit vs 64bit) on the machine, and has more to do with the ethernet controller not being up at install time. I've seen similar posts for other platforms (notably ARM)  that have the same problem and no ethernet.

---

### Post by dcstar on 2010-02-27
> **mgrosvenor said:**
> I have also had this problem. I'm running VMware fusion on an on a Mac. I have a feeling this has nothing to do with the word size (32bit vs 64bit) on the machine, and has more to do with the ethernet controller not being up at install time. I've seen similar posts for other platforms (notably ARM)  that have the same problem and no ethernet.

All Ubuntu installs give you the option of entering Proxy settings for those environments that do not have a direct Internet connection. If you do not set this correctly, or do not have an Internet connection then the install process will stall with continual timeouts trying to get the latest updates from the Ubuntu servers. If you have no network then it will not attempt these updates.

This has nothing whatsoever to do with virtualization, it is a basic installation issue.

---

