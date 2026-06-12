---
title: "Should I install Ubuntu alongside Windows 8?"
date: 2015-06-29
forum: Ubuntu, Linux and OS Chat
---

### Post by dejomasters on 2015-06-29
This isn't really a problem, I just wanted some insight. I currently run Ubuntu 15.04 on my laptop, and I've loved using it. I recently built a custom PC (for work and gaming) and put Windows 8.1 on it. I've been tossing around the idea of dual booting for a while, but I don't know if I should. I've never tried dual booting a PC before, and I don't want to screw something up and erase or corrupt the 500GBs of data I already have. Then again, Ubuntu is one of my favorite, if not my all time favorite, operating systems. Should I just stick with it on my Laptop or dual boot?

---

### Post by Bucky Ball on 2015-06-29
Welcome. Always back up all data prior to doing anything like this if you want to be guaranteed there will be no less. Doesn't matter how sure you are things are going to work, mistakes can and do happen.

If you want support with how to dual-boot, best to post a thread in ***Installations & Upgrades***, but basically, you are going to need to backup valuable data, possibly shrink the Windows partition to leave free space to install Ubuntu and a /swap file, then install using 'Something Else' when you get to the partitioning section.

Use Win software to resize Win partitions, Gparted for Ubuntu partitions. 

As to whether or not you should dual-boot, only you can answer that question. There's nothing stopping you, put it that way. The main rule of thumb is have a solid mudmap of how you want your hard drive partitioned BEFORE booting up and trying to figure it out while you're sitting in front of the machine. Make a plan. Good luck whatever you do.

---

### Post by mattharris4 on 2015-06-30
I would go ahead and attempt a dual-boot on that computer.  The issue with the computer only booting Windows seems to come up on HP computers as well as some Toshibas and Sonys.  I don't have experience with installing on a custom-built computer but cannot imagine that a motherboard manufacturer would install a UEFI that blocks other OSes considering they don't provide one with purchase.  

I do have a dual-boot with Win 8.1 and Lubuntu on my laptop (a Toshiba of all things, I must have got lucky and bought one without the UEFI dual-boot issue), it installed without major issue and I don't have any issues attributable to either OS (it does have a slow CPU in it).

I do agree with Bucky Ball that you need a backup copy of your files, your Windows install disks and the license number on the Windows install just in case you do bork your hard drive and have to start from scratch.  As long as you pay attention and don't select the option to install Ubuntu alone you should not mess up that install but unfortunately stranger things have happened on rare occasion.

---

### Post by grahammechanical on 2015-06-30
You could do what some other people have done. They have installed Ubuntu and erased Windows at the same time and then changed their minds and without having a Windows install disc ask us how to get Windows back. You paid for Windows. Keep it. You are bound to want it back the moment you erase it. All it is doing is taking up disk space. You could have a partition that is formatted NTFS and then both Windows and Ubuntu can access the data in it.

Regards.

---

### Post by buzzingrobot on 2015-07-01
Partitions can be resized (see gparted).  So, one option might be to set up dual booting, then shrink the Windows partitions to some very small size. Then, if you later decide you want to make more use of Wndows, you can shrink the Ubuntu partition and expand Windows.  That would avoid the hassle of a reinstall, possible activation hassles, etc.

Also, if you install Windows 8.1 now, you will be prompted during the install and asked if you want to opt in to upgrading to Win10 later.

---

