---
title: "Running 64 bit in Virtual Box?"
date: 2019-10-31
forum: Virtualisation
---

### Post by Fred_Zyzoff on 2019-10-31
Is there a 32-bit Ubuntu or Kubuntu server ISO for 19.10? I aRunningm running Kubuntu on my box where lscpu tells me it's 64-bit (see below)
    
    I also run Virtualbox where I have a VM for Win7-32bit. 

I tried to install Ubuntu server 19.10, 64-bit but it would not allow that, so I instead installed Ubuntu server 16.04 32-bit. Nothing newer seems to have a 32-bit package. Or if they do exist, anyone know where to find them?

I also want to install either ubuntu or kubuntu 19.10 desktop, but am concerned that VirtualBox might not allow those as well (even though it supposedly allows 64-bit installs).
    
    
> root@mybox:/home/me# lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                8
On-line CPU(s) list:   0-7
Thread(s) per core:    2
Core(s) per socket:    4
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 58
Model name:            Intel(R) Core(TM) i7-3770K CPU @ 3.50GHz
Stepping:              9
CPU MHz:               1600.019
CPU max MHz:           3900.0000
CPU min MHz:           1600.0000
BogoMIPS:              7020.82
Virtualization:        VT-x

---

### Post by deadflowr on 2019-10-31
[I]Thread moved to **Virtualization**
[/I]
No.
32-bit images have been dropped.
And to top that off, Ubuntu has dropped all but a small selection of 32-bit packages for 19.10
[https://ubuntu.com/blog/statement-on-32-bit-i386-packages-for-ubuntu-19-10-and-20-04-lts]("https://ubuntu.com/blog/statement-on-32-bit-i386-packages-for-ubuntu-19-10-and-20-04-lts")

That said, your system is beefy enough to easily handle 64-bit vms.
What exactly happens when you try installing the 19.10 server?

---

### Post by guiverc on 2019-10-31
Most flavors (inc. Kubuntu) provided x86 ISOs for 18.04 LTS, but they are desktop releases; ie. there is no Kubuntu server ISO.  

Ubuntu 18.04 also had a netboot option in x86 ([http://archive.ubuntu.com/ubuntu/dists/bionic-updates/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/bionic-updates/main/installer-i386/current/images/netboot/)) 

(*Two flavors also produced 18.10 x86 ISOs, but they both stopped spinning 19.04 ISOs in Dec-2018 so for full support on x86, returning back to 18.04 LTS provides a longer supported life as 18.04 flavors have support till 2021-April, where as 18.10 is EOL already & 19.04 hasn't long left and neither flavor officially supported x86 in 19.04 anyway..*)

---

### Post by Fred_Zyzoff on 2019-10-31
Thanks to both deadflowr and guiverc for your replies. Yes, my hardware should do that. My main OS is Kubuntu 15.10. (yes, I should have upgraded a long time ago, but life got in the way).

According to hostnamectl, the Architecture: x86-64. When I installed VirtualBox, I used ver. 5.0.40 which should be able to handle 64-bit. Up until yesterday, the only VM I had set up was an old copy of Win7 (32-bit), essentially for a few Win apps without suitable linux alternatives. I don't recall if the 32-bit Win7 was used because that's what I had, or if limited by VirtualBox.

So I'm hoping to set up the recent server and desktop releases as VMs for testing. (I also run Debian on an off-site server). Obviously I'd prefer using 64-bit.

To answer deadflowr's question, I'll attempt to reinstall the 19.10 server (64-bit) and will report back on what happens. Thanks again.

UPDATE: the first time I tried to install 19.10 64-bit in VirtualBox, I was able to get much further, even got a terminal message (from within VirtBox) saying the install could not be completed. But this time, after clicking "New" and entering the OS name and choosing "Linux" as the type, the only allowable versions are all 32-bit. So could it be that my version of VirBox isn't aware of, or can't handle 64-bit? Using VirtBox 5.04.

---

### Post by ajgreeny on 2019-10-31
You have both an unsupported version of your host OS (15.10) and an unsupported version of VirtualBox, so I believe it is very important for you to update or reinstall both.

If your hardware is strong enough and can run 64bit systems without a problem you should not have any major difficulty running a VM of a 64bit guest; check that you have virtualisation (VT-x or AMD-V) properly enabled in the BIOS/UEFI settings of your host machine.

---

### Post by Fred_Zyzoff on 2019-10-31
Thanks ajgreeny. That is exactly what I'm working up to doing, update everything. That's why I hope to install 19.10 as VMs for testing. I'm pretty sure that virtualization is enabled in the BIOS, but will check again next time I reboot. Thanks.

---

### Post by SeijiSensei on 2019-10-31
Check that you have enabled all the virtualization features in the BIOS.  To run 64-bit VMs, the host must also support 64-bit.  If you're running 32-bit Ubuntu on the host, you'll need to install a 64-bit version to run 64-bit VMs.

---

### Post by Fred_Zyzoff on 2019-10-31
Thank you ajgreeny and SeijiSensei. I thought for certain that vitualization had been enabled, but what do you know.... on a reboot and checking the BIOS, it wasn't. It now is and of course, In the BIOS (Asus P8Z77-V Deluxe Mobo), it's called Intel Virtual Tech.

Vbox now allowed 64 bit installs. So I installed v19.10 pretty easily.

One change I made -- as this is primarily for testing, was to create a VMDK instead of a VDI disk. Also instead on one file, I had it split the file into 2GB chunks.

This solves another big problem I've had, although I haven't seen any discussion of this on google searches.

With my Win7 VM, the disk file is about 40GB. Along with everything else in my workstation (and off-site server), this gets backed-up to Backblaze. During these operations, most files are just synced (not rewritten) to Backblaze. But a 40GB file with new data gets completely rewritten, and can take several hours to accomplish. And if there's a hiccup along the way, it starts all over. I'm hoping with the VM file split into chunks, backups will go much quicker.

In any case, this seems to solve my immediate problem. Thanks to all who replied.

Now I get to try to install the desktop 19.10 64-bit.

---

### Post by ajgreeny on 2019-10-31
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by deadflowr on 2019-10-31
As you've found out why it wasn't working and the fix, please go ahead and [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

ninja'd by ajgreeny.

---

