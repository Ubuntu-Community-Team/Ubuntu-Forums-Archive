---
title: "Can't boot after Ubuntu Server installation"
date: 2008-08-07
forum: Server Platforms
---

### Post by Mauzer on 2008-08-07
Hey everyone,

I've been trying to install Ubuntu server serveral times. At the end of the installation it will reboot my pc and try to launch Ubuntu but I get the "reboot and select proper boot device or insert boot media in selected boot device"-message.

My boot device is a 80GB IDE Maxtor harddisk which I have specified during the setup to put Ubuntu on. I also have a 320GB SATA Western Digital harddisk, which I want to use with Samba. This disk doesn't show up in my bios (as master or slave), but is has been working fine under Windows XP.

In a desperate attempt I've tried to install Ubuntu onto this harddisk, but I ended up with the same message. I am currently installing XP again to fix the partitions again, but I hope someone can give me proper instructions to make this work again.

This has all give me a bit of extra time to think about things and I've come to the conclusion that I'd rather have Ubuntu server installed on my 320GB disk since I'll most likely replace my 80GB IDE disk soon to a xTB SATA disk.

Thanks in advance,
 Maurice

---

### Post by windependence on 2008-08-07
You need to get your devices straight in the BIOS for this to work. make sure your boot disk is the one listed in the BIOS as your first boot device.

-Tim

---

### Post by Mauzer on 2008-08-07
The Maxtor harddisk is selected as my first boot device in my bios. The other option is my cd drive.

---

### Post by windependence on 2008-08-07
Is the Maxtor where you have Ubuntu loaded? If so, you might try re-installing grub on that drive.

-Tim

---

### Post by Mauzer on 2008-08-07
I've tried installing Ubuntu on both disks, but most of my attempts were on my Maxtor. My Maxtor disk is /dev/sdb while my Western Digital is /dev/sha. I'll reinstall Ubuntu server on my Maxtor and try to reinstall GRUB after, but I think I've tried that before if I remember correctly. I've tried so many things before giving up and asking for help here... ;-)

Edit: I tried installing Ubuntu on (hd0) and /dev/shb without success.

---

### Post by Mauzer on 2008-08-08
Anyone?

---

### Post by Mauzer on 2008-08-10
I'm clueless. If noone can help me out I'll have to go back to win xp...

---

### Post by cariboo on 2008-08-10
If your Maxtor disk shows up as /dev/sdb then it is setup as a slave. Check the jumpers and make sure it is the master. Your Western Digital is a wierd dev it should be /dev/sdb. I would check your cables and jumpers Make sure that which ever drive you use for your installation is set to be the master and your data drive set to slave, and make sure they show up in your bios in the right order.

Jim

---

### Post by Mauzer on 2008-08-11
My Maxtor disk is a 6Y080P0 and I have it configured as master according to [this jumper guide](http://seagate.custhelp.com/cgi-bin/seagate.cfg/php/enduser/std_adp.php?p_faqid=1227&p_created=1031610289). I have tried both master and cable select. In my bios it is selected as my Primary IDE disk and it's the only disk that shows up in my boot sequence menu (next to my cd-rom drive).

However during the Ubuntu installation it is detected as the following:

SCSI2 (0,0,0) (sda) - 320.1 GB ATA WDC WD3200KS-00P
SCSI3 (0,0,0) (sdb) - 82.0 GB ATA Maxtor 6Y080P0

Because the Western Digital disk is a SATA disk I can't use the jumpers to set it as slave. See [here](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=1400&p_created=1134597011).

---

### Post by guilly on 2008-08-11
If it's being detected as SDA then that's perfectly fine. 

I woudl try and install Ubuntu again with your 320, and just to be sure disconnect your 80 during the install.

---

### Post by Mauzer on 2008-08-19
Didn't work either. Like I said earlier, the sata disk doesn't show up in the bios. Going to look for a bios update now, hopefully that will make a difference. I'll post as soon as I know more. If anyone has any other ideas please let me know.

P.S. I've been busy the past week, hence I didn't get to try the last suggestion earlier.

---

### Post by Mauzer on 2008-08-19
Success. I have the Asus K8V MX motherboard and I was running revision 0201 of my bios. I found a rom file with revision 0211 on the Asus website and I also downloaded afudos, the utility to update your bios with. Then I turned a usb stick into a boot disk with win98 on it and I ran afudos.exe with the rom file. Then I rebooted and grub did the rest.

Thanks everyone for your help!

---

