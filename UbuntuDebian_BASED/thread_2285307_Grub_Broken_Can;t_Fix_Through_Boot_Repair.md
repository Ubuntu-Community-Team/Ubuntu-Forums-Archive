---
title: "Grub Broken Can;t Fix Through Boot Repair"
date: 2015-07-04
forum: Ubuntu/Debian BASED
---

### Post by Grubz on 2015-07-04
Been Working With Boot Repair All Morning & Retesting To See If I Can Boot I Constantly Get Errors Such As "error:unknown filesytem" "error:filesytem not found" and etc here's my bootinfo summary [http://paste.ubuntu.com/11822678/](http://paste.ubuntu.com/11822678/)
Please help

---

### Post by ubfan1 on 2015-07-04
Grub got badly confused by all your USB storage (sdb-e).  You should be able to edit the grub.cfg file (either from the live media, or just at the grub command line (type e at the menu) and change all references to hd2 to hd5 (sdf=5, since disks start at hd0).  At the first successful boot, immediately run sudo update-grub in a terminal (type crtl-alt-t to bring up a terminal).  That should fix the problem.

---

### Post by Grubz on 2015-07-04
Tried to edit my grub.cfg says I don't have permissions to edit the file.

---

### Post by Grubz on 2015-07-04
exacty error is "cannot open write to file"

---

### Post by oldfred on 2015-07-05
Moved to Other OS since Kali.

You almost never directly edit grub.cfg.
You either do one time edits as you boot at grub menu.
Or you change other grub files and run sudo update-grub to refresh grub.cfg with changes. But that only works from inside working install or a chroot.
Only very occasionally might you need to directly edit grub.cfg, but it is write protected and you have to both turn off write protection and use sudo.


Since you have several drives, do not run any auto fixes in Boot-Repair. You only want grub in the drive shown as sdf and you want a Windows boot loader in the drive shown as sdg.

Not sure why drives are sdf & sdg?

Boot drive with BIOS/grub is always hd0 in grub. 
Then each drive is in the order you typically see in Linux. And that was with my systems the order plugged into the SATA ports.
 
When you boot, use e for edit and change this to hd0.
 set root='(hd2,msdos1)'

Or do change first Ubuntu boot stanza in grub.cfg which is not normally suggested.
      
 #Normally we do not directly edit grub.cfg. Edit from live-CD/DVD/USB.
mount /dev/sdf1 /mnt
sudo nano /mnt/boot/grub/grub.cfg
#May have to do this first as it is write protected also:
sudo chmod +w /mnt/boot/grub/grub.cfg
#Or even this first:
sudo chmod 777 /mnt/boot/grub/grub.cfg

Be sure to then boot sdf drive, if you use grub in Windows drive to boot then hd0 may be hd1 or hd2?
And use Boot-Repair's advanced mode or your Windows repair flash drive to restore a Windows boot loader to the MBR of your Windows drive so you can directly boot from BIOS.

---

