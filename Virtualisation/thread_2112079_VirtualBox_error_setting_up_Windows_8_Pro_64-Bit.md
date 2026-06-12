---
title: "VirtualBox error setting up Windows 8 Pro 64-Bit"
date: 2013-02-03
forum: Virtualisation
---

### Post by digitaldecimator on 2013-02-03
I have been having some trouble setting up my virtual machine with windows 8 professional edition via VirtualBox. After allocating RAM and Hard Disk space I attempted running the Windows 8 setup from an iso disk image and after about 30 seconds of sitting at the bootup screen I get an error and it tells me that my pc needs to restart. Could this be an issue with windows 8 support? I am running Ubuntu 12.10 64-Bit by the way. I am quite new to virtualization so any help is much appreciated. Thank you very much.

---

### Post by SeijiSensei on 2013-02-03
How much memory did you allocate?  I usually give Windows 7 1.5 GB at a minimum.  I've never installed Win 8.

Remember that when the Windows installer in the VM talks about restarting, it means restarting the virtual machine, not the host computer.  It cannot see outside the VM box and has no idea that it is not being installed on a physical machine.

Does the error have a numeric code associated with it?  If so, write it down and look it up online.

Also there are [many postings]("https://www.google.com/search?q=virtualbox+64-bit+windows+on+64-bit+ubuntu") about problems with 64-bit Windows in a VirtualBox VM.  Maybe some of them have solutions to the problems you are facing.

---

