---
title: "Can't reinstall grub2."
date: 2013-05-06
forum: Ubuntu Development Version
---

### Post by markdark20 on 2013-05-06
Today, my burg was freeze on loading. So im tried to reinstall grub by an Ubuntu liveCD 13.04 disk.
by these command below:
```
sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
grub-install --boot-directory=/mnt dev/sda
update-grub
```
everything is success and then I reboot my laptop, but 'grub screen' only show me grub prompt, no menu to select.
I try to boot to ubutnu by grub prompt:
```
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
set
insmod /boot/grub/i386-pc/linux.mod
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot

```

oK, my ubuntu is booting up , and I reinstall grub:
```
sudo grub-install --boot-directory=/ /dev/sda
sudo update-grub
```

 ```
grub-install -v
```
grub-install (GRUB) 2.00-13ubuntu3



everything is sussess
But when I reboot my laptop, still grub prompt.

```
fdisk -l 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   128018431    64008192    7  HPFS/NTFS/exFAT
/dev/sda2       128021985   976768064   424373040    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       128022048   149002874    10490413+  83  Linux
/dev/sda6       149002938   211929479    31463271   83  Linux
Partition 6 does not start on physical sector boundary.
/dev/sda7       211929543   358731449    73400953+   7  HPFS/NTFS/exFAT
Partition 7 does not start on physical sector boundary.
/dev/sda8       358731513   685429289   163348888+   7  HPFS/NTFS/exFAT
Partition 8 does not start on physical sector boundary.
/dev/sda9       685429353   829966094    72268371    7  HPFS/NTFS/exFAT
Partition 9 does not start on physical sector boundary.
/dev/sda10      829966158   967145129    68589486    7  HPFS/NTFS/exFAT
Partition 10 does not start on physical sector boundary.
/dev/sda11      967145193   976768064     4811436   82  Linux swap / Solaris
Partition 11 does not start on physical sector boundary.
```


Please help me reinstall grub on my Ubuntu 13.04 x64
OR Please help me install another grub version like
**grub2_1.99-21ubuntu3.9_amd64.deb**

from [http://packages.ubuntu.com/precise-updates/amd64/grub2/download](http://packages.ubuntu.com/precise-updates/amd64/grub2/download)
(because grub2 on my laptop can't booting to Windows 7 , now. but burg can do.)

thanks so much.
Sorry, my english is very bad.

---

### Post by oldfred on 2013-05-06
If you can boot manually, you can do this:
 sudo grub-install /dev/sda
      
 sudo update-grub

Sometimes this works better:
      
 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

If you still have issues, download Boot-Repair and run the BootInfo report.
      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by grahammechanical on 2013-05-06
Do you understand why it failed? You updated the Grub configuration files but you did not install Grub into the MBR of sda. It is the ```
sudo grub-install /dev/sda
``` that does it.

Regards.

---

### Post by ventrical on 2013-05-06
I have the grub-rescue CD and that does it every time.

---

### Post by markdark20 on 2013-05-06
Thanks you so much ^^
I mistake here : 
sudo grub-install [SIZE=2]**--boot-directory=/**[/SIZE] /dev/sda
code correct is 
sudo grub-install /dev/sda

But now I have a new problem, grub2 cann't bootting correct to Windows7. It show BOOTMGR is corrupt. The system cannt boot.

If I use Restore MBR of boot-repair tool, the system straight boots to Windows7 without grub menu.
Ìf I use Reinstall Grub (boot-repair), grub menu cann't boot to Windows7 like I said above.
What's I need to do to repair grub (and boot corect to W7, too) ?
Thanks

---

### Post by oldfred on 2013-05-06
Boot-Repair will not fix Windows internal errors, It can add a Windows boot loader to the MBR. You will need your Windows repairCD or flash drive. Or some have gotten into Windows 7 repair console if booting the 100MB boot/repair, but you have to be very fast (same time) with f8 as the time from grub to Windows is a lot shorter than from MBR to Windows booting. Some said they had to try many times just to get it to work once. Probably better to have Windows repairCD or flash drive.

BootInfo report may show some of the Windows issues. Often chkdsk is needed from Windows repairs.  If you installed grub to Windows PBR Bootinfo report will show that, but you can use testdisk on a Linux live installer to fix that. Then everything else is Windows repairs.

---

### Post by Rukiri on 2013-05-07
grub-install --boot-directory=/boot --no-floppy --recheck --debug /dev/sda
grub-mkconfig -o /boot/kernel-3.9.0 

reboot

you should now be greeted with grub.

---

### Post by markdark20 on 2013-05-07
thanks
here is my Bootinfor 
[http://paste.ubuntu.com/5640543/](http://paste.ubuntu.com/5640543/)

I will try testdisk and report back later.

---

### Post by markdark20 on 2013-05-07
My problem is solved.
I use BootICE and Parted Magic to fix Windows loader and grub2.
Thanks all ^^

---

