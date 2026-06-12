---
title: "Can I install windows from recovery CD's in a vm"
date: 2012-10-12
forum: Virtualisation
---

### Post by kaloasd on 2012-10-12
I have a laptop with 6G ram i5 2.5GH and am wondering if I could install Windows in a VM. The Windows was installed on the same laptop.

---

### Post by afz12 on 2012-10-12
Hi kaloasd

I suspect you may have problems using "recovery CD's". From past experience these are not complete install CDs - instead they may just "point" to a partition on your hard drive that contains the windows installation. This may depend on your system. Also, I have one notebook that used to run Vista (now Ubuntu 12.04). It had a "glitch" and the recovery CDs didn't work. It turned out that this model (Acer 5920) had a known problem with this! However it did have a separate partition for the windows installation but it turned out to be unusable for recovery.

I found a similar approach on this notebook (also now Ubuntu 12.04 - waiting to upgrade to 12.10 next week perhaps). It ran into a muddle with Win7 and it was easier to remove it and use Virtualbox for other OS. It also had a separate partition for the windows install but this turned out to be unusable. I had made "recovery CDs" but when needed, they failed!

You may find some way to install windows as a Virtual Machine (VM) on Virtualbox, VMware etc, but I suspect it will be a mission. You may find the "recovery" disks and partition will not be recognized as a OS, or if you get this to work, you may find it impossible to "activate" or register etc.

Your best bet, my guess, is to find a bone-fide windows installation disk and go from there. Even so, Win7 appears to be sold as an "upgrade" so you might need to start with a Vista install CD first (or worse, a XP installation).

I don't mind windows as some programs I use aren't available on Linux. However most of the time I use Ubuntu or Mint (Mate, Cinnamon). XP is perfectly adequate for this - perhaps you can find an install CD (or USB stick or file) for XP and VM this? The only problem with XP is that is usually 32 bit and some things I play with really need 64 bits.

Good luck - it will be interesting to read if anyone has a solution to your question.

---

### Post by Cheesemill on 2012-10-13
No, you can't.

Recovery CD's are linked to the actual physical hardware of your laptop, trying to use them for a VM won't work as the VM presents different hardware to the guest OS.

---

### Post by kaloasd on 2012-10-13
Thanks for the replies.

I may need to clarify. I have 5 recovery DVDs. I saw a tutorial on how to do something similar with disk2vhd and I wanted to know if I could do it with the dvds because it's a cleaner version of the OS.

---

### Post by dcstar on 2012-10-13
> **kaloasd said:**
> Thanks for the replies.

I may need to clarify. I have 5 recovery DVDs. I saw a tutorial on how to do something similar with disk2vhd and I wanted to know if I could do it with the dvds because it's a cleaner version of the OS.

Just install Windows as normal and use a free tool like VMware's Converter to turn it into a VM.

---

### Post by coldraven on 2012-10-13
> **Cheesemill said:**
> No, you can't.

Recovery CD's are linked to the actual physical hardware of your laptop, trying to use them for a VM won't work as the VM presents different hardware to the guest OS.
Wrong. I have XP running in a VM from a recovery disc. You can use ```
dmidecode
```to get the strings you need then make a bash script to create a "fake" VM bios simialr to this
```
#! /bin/bash
VM_NAME="xp01" # Name of your Virtual Machine
VSETED="VBoxManage setextradata $VM_NAME"
CFG_PATH="VBoxInternal/Devices/pcbios/0/Config"
$VSETED $CFG_PATH/DmiBIOSVendor       "Hewlett-Packard"
$VSETED $CFG_PATH/DmiBIOSVersion      "F.0C"
$VSETED $CFG_PATH/DmiBIOSReleaseDate  "06/05/2008"
$VSETED $CFG_PATH/DmiBIOSReleaseMajor  "15"
$VSETED $CFG_PATH/DmiBIOSReleaseMinor  "12"
$VSETED $CFG_PATH/DmiBIOSFirmwareMajor "113"
$VSETED $CFG_PATH/DmiBIOSFirmwareMinor "45"
$VSETED $CFG_PATH/DmiSystemVendor     "Hewlett-Packard"
$VSETED $CFG_PATH/DmiSystemProduct    "HP Compaq 6715b"
$VSETED $CFG_PATH/DmiSystemVersion    "<RK154AV>"
$VSETED $CFG_PATH/DmiSystemSerial     "XXXXXXXXX"
$VSETED $CFG_PATH/DmiSystemUuid       "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX"
$VSETED $CFG_PATH/DmiSystemFamily     "103C_5336AN"
```
You must run the script after creating the virtual disc but before installing Windows
I got this from the VirtualBox forum

---

### Post by Cheesemill on 2012-10-13
I stand corrected.

However, you will still be breaking your Windows EULA and therefore not be running a legal copy of Windows.

---

### Post by kaloasd on 2012-10-13
Thank you all for the responses.

I used disk2vhd to convert it. Now I'm getting an unknown file system error and am trying to fix it.

---

### Post by coldraven on 2012-10-14
> **Cheesemill said:**
> I stand corrected.

However, you will still be breaking your Windows EULA and therefore not be running a legal copy of Windows.
Many EULAs are not legally applicable.
I do not think that under UK law it would be illegal to run the software that I paid for with this laptop virtually rather than normally.
As XP is prone to  breaking,  it is far easier to just reinstall from a saved VM than spend hours doing a full install. In fact I very rarely use it at all.
Anyway I don't think that Microsoft is going to track me down and sue me :)

---

### Post by Paddy Landau on 2012-10-15
Another possible solution is to have Virtual Box run the installed Windows on your computer in a virtual environment.

However, be advised that it is quite complex to set this up, and if you make a mistake you are likely to break your Windows installation. If you want to try this, first back up your Windows installation using [CloneZilla]("http://clonezilla.org/") (so you can restore it if you break it), and then follow the instructions carefully.

---

