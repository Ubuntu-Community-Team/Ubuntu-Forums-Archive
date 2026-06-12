---
title: "Ubuntu 14.04 and Windows 8.1 question"
date: 2015-07-09
forum: Ubuntu, Linux and OS Chat
---

### Post by sports fan Matt on 2015-07-09
Just a quick question.  A few weeks ago, I was in a local computer store and I heard the clerk say to a customer "Never put Linux on a dual boot Windows 8 install, it won't ever run right". I can see where the store employee is coming from because you'd erase the boot loader but there are ways to get it back.

Was the employee too harsh to the customer?

---

### Post by makitso on 2015-07-09
> Was the employee too harsh to the customer?  Yes -- must have been Best Buy :-)  

Honestly, I run 8.1 and 14.04 on a dual boot Lenovo Thinkpad 450S.  The setup was a bit tricky but it works just like any other dual boot system I have had.

---

### Post by mastablasta on 2015-07-09
depends on the UEFI. as well as how it is all setup. it can happen that boot loader get overwritten or if you leave windows hibernating or fast boot some strange things could occur. I am sure everything is solvable. but for the average user they might have issues. good backup can provide a fall back. I would advise the same to a normal user-> not to get into the dual boot arena.

edit: here is another strange thing - I am not sure if running win8 would solve it but with win7 and traditional BIOS - in Windows time is 13:00 in Linux time is 16:00 on same PC. no so good if you have some sync and files where it would replace the "old" files or you need to keep changing the time.

---

### Post by oldfred on 2015-07-09
There is a bug on reinstall of Ubuntu with Windows 8 that does erase system.
 Reinstall says overwrite Ubuntu but it also erases existing Windows or any other partitions.
Sept 2014 Fix being released for one drive installs, but multiple drive installs must use Something Else. And fix is not in current versions. Perhaps in 15.04.
this bug was fixed in the package ubiquity - 2.18.8.3 jan 2015
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

But we have seen many users with just about every brand of system, install Ubuntu to Windows 8 systems. Some install easier than others.

But with UEFI, installing Ubuntu does not erase Windows dual boot. All systems installed share the efi partition. 
With BIOS you only have one MBR, so only one system can control booting. But MBR is easily updated.

So employee was just trying to sell Windows. Often stores & vendors are only set up to support Windows, so want to discourage other systems as they just to not know them.

While I have helped a lot of users dual boot, my own install with Windows on a Dell SFF system was about as easy as it can be. While it took a lot to do all the backups, even a Windows only user should do those backups. I used Windows to shrink Windows. That took me a bit as not familiar with new Windows and rebooted so it could run chkdsk. Turned off fast startup. Then used gparted to create partitions. And used Something Else to install. Actual install to partitions that were already created took only about 10 minutes which surprised me as it was just a hard drive not a SSD.

---

### Post by grahammechanical on 2015-07-09
What a retailer does not want is a customer coming back and asking for their money back because the machine is broken. But why is it broken? Because the customer tried to install Linux and perhaps erased the disk as part of the install process. Or, messed up in some other way.

And as we see on these forums it is possible to get into difficulties trying to dual boot Linux and Windows. I am surprised that installing another OS does not invalidate the warranty.

Regards.

---

### Post by sports fan Matt on 2015-07-09
Agreed Graham, and it was Staples

---

