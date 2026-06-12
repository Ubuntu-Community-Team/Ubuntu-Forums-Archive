---
title: "Can't Format Floppy bug ?"
date: 2011-11-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2011-11-15
My apologies... I was just trying to follow up on a suggestion concerning another Precise matter and found that  I can't even format my floppy drive:

I'll try another machine or my USB floppy.

---

### Post by ventrical on 2011-11-15
Screenshot:

---

### Post by coffeecat on 2011-11-15
Floppies?! I'll never keep up with the march of technology! :(

:wink:

Yes, I get this too. I've posted a screenshot with the details drop-down.

I see that floppies still will not automount from the GUI, a bug that's been with us since 10.04, if not 9.10. I have to use "udisks --mount /dev/fd0".

---

### Post by ventrical on 2011-11-15
> **coffeecat said:**
> Floppies?! I'll never keep up with the march of technology! :(

:wink:

Yes, I get this too. I've posted a screenshot with the details drop-down.

I see that floppies still will not automount from the GUI, a bug that's been with us since 10.04, if not 9.10. I have to use "udisks --mount /dev/fd0".

Thanks for that confirm. I was trying to move/copy the superegrub2.iso  1.44MB file as was suggested in another thread. I know it will work in Windows XP :lol :)

That is : super_grub_disk_hybrid-1.98s1.iso

 I have this unique little USB floppy drive by SONY that will let me get into  any PC (practically) and all those neat linux disks are great tools to have, especially now since Precise will start to break soon (it is postulated and assumed) :)

---

### Post by teh603 on 2011-11-15
> **coffeecat said:**
> I see that floppies still will not automount from the GUI, a bug that's been with us since 10.04, if not 9.10. I have to use "udisks --mount /dev/fd0".Wait, floppies are capable of automounting? I thought that was only possible on the older Macs, and PC- platform stuff including Linux PCs had to manually poll the drive every time someone put a disk in.

Then again, I've never had a floppy drive since my Powerbook 3400 kicked the bukkit, so.... /sweatdrop

---

### Post by coffeecat on 2011-11-15
> **teh603 said:**
> Wait, floppies are capable of automounting? 

Sorry - bad wording on my part. I meant that the desktop won't automount floppies. When I click on the floppy icon in the left pane of Nautilus in Pangolin, the system does nothing. If I ctrl-L and "computer://" to get the old Computer file-browser and double-click on the floppy icon, I get an error message. The same or equivalent has been happening since Lucid.

---

### Post by ventrical on 2011-11-15
Disk utility will detect Y-E data USB floppy but it is absolutely useless. Can't format ..etc... Cairo Dock acts like a plug 'n play pop-up with this floppy .. but still can't do nothing with Precise.

 So, in the Ubuntu scheme of things, the floppy is pretty well obsoleted. Sad , really.

---

### Post by effenberg0x0 on 2011-11-15
> **ventrical said:**
> Disk utility will detect Y-E data USB floppy but it is absolutely useless. Can't format ..etc... Cairo Dock acts like a plug 'n play pop-up with this floppy .. but still can't do nothing with Precise.

 So, in the Ubuntu scheme of things, the floppy is pretty well obsoleted. Sad , really.

Maybe the floppy disk was formatted in DOS/Windows, in which case you would have to mount it using a specific file system? So that you can later format it using ext2/3/4 (or keep it mounted using FAT if you chose to)? 

*sudo mkdir /mnt/floppy && sudo mount -o umask=0 -t vfat /dev/fd0 /mnt/floppy*

Also, I think nautilus can't mount a floppy if it's not ran as root. Having the unit parameters on fstab might help, but I think you still need to be root. 

Just guessing here, I don't have a floppy...

---

### Post by ventrical on 2011-11-16
The supergrub2 .iso file is 1.44MB file. On windows the image can be safely moved/copied from disk to floppy.  I was able to get it on CD.  I use the USB floppy I have to run PLOP bootloader on machines that will not bootup from pendrives.  Someone recommended I download supergrub2 and I just think that it is a waste of a lot of space on 1 CD being that I can't use Precise (or any other Ubuntu) to copy that image to a 1.44 floppy.)

Kfloppy  loaded and actually worked in the GUI but would not work either (internal error). while trying to format.


  It's not a problem .. I'll just use MSwindows .. but I was trying to get away from having to do this as I want to be able  to do these simple tasks with Precise. 

  I'll try your code out.

Thanks effenberg.

---

### Post by plucky on 2011-11-16
As it is an image file,try from a terminal ```
sudo dd if=super_grub_disk_hybrid-1.98s1.iso of=/dev/fd0
``` as long as the image file is your /home directory.

The result is ```
2820+0 records in
2820+0 records out
1443840 bytes (1.4 MB) copied, 99.5127 s, 14.5 kB/s
```

Then try to boot the floppy.

This worked on my internal floppy on Pangolin,cannot vouch if it will work on an external floppy.

Good Luck

---

### Post by effenberg0x0 on 2011-11-16
> **plucky said:**
> As it is an image file,try from a terminal ```
sudo dd if=super_grub_disk_hybrid-1.98s1.iso of=/dev/fd0
``` as long as the image file is your /home directory.

The result is ```
2820+0 records in
2820+0 records out
1443840 bytes (1.4 MB) copied, 99.5127 s, 14.5 kB/s
```Then try to boot the floppy.

This worked on my internal floppy on Pangolin,cannot vouch if it will work on an external floppy.

Good Luck

DD is a good choice. I just don't know how / if the thing is mounting there, as USB or FD?

@Ventrical Question: Does a USB-Floppy show as a normal floppy (fd0) or as a USB device (sb0) on sudo lshw? 

One other thing: I SSHd to a machine that I know has an *internal* floppy running Maverick. In that machine, the Kernel module "floppy" is being loaded at boot in /etc/modules (was manually added). So that kernel version didn't have it by default. You probably want to check there. If it's not, sudo modprobe floppy would load it.

---

### Post by ventrical on 2011-11-16
> **effenberg0x0 said:**
> DD is a good choice. I just don't know how / if the thing is mounting there, as USB or FD?

@Ventrical Question: Does a USB-Floppy show as a normal floppy (fd0) or as a USB device (sb0) on sudo lshw? 

One other thing: I SSHd to a machine that I know has an *internal* floppy running Maverick. In that machine, the Kernel module "floppy" is being loaded at boot in /etc/modules (was manually added). So that kernel version didn't have it by default. You probably want to check there. If it's not, sudo modprobe floppy would load it.


 Pangolin morning surprise .... I can't open a terminal !! :)

Time for reboot. lol :)

---

### Post by ventrical on 2011-11-16
> **effenberg0x0 said:**
> DD is a good choice. I just don't know how / if the thing is mounting there, as USB or FD?

@Ventrical Question: Does a USB-Floppy show as a normal floppy (fd0) or as a USB device (sb0) on sudo lshw? 

One other thing: I SSHd to a machine that I know has an *internal* floppy running Maverick. In that machine, the Kernel module "floppy" is being loaded at boot in /etc/modules (was manually added). So that kernel version didn't have it by default. You probably want to check there. If it's not, sudo modprobe floppy would load it.


 It will not detect the standard floppy but I get this when I stick in the USB floppy:


   *-scsi
          physical id: 1
          bus info: usb@3:2
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb

---

### Post by ventrical on 2011-11-16
> **plucky said:**
> As it is an image file,try from a terminal ```
sudo dd if=super_grub_disk_hybrid-1.98s1.iso of=/dev/fd0
``` as long as the image file is your /home directory.

The result is ```
2820+0 records in
2820+0 records out
1443840 bytes (1.4 MB) copied, 99.5127 s, 14.5 kB/s
```Then try to boot the floppy.

This worked on my internal floppy on Pangolin,cannot vouch if it will work on an external floppy.

Good Luck


dale1@ubuntu:~$ sudo dd if=super_grub_disk_hybrid-1.98s1.iso of=/dev/fd0
[sudo] password for dale1: 
dd: opening `/dev/fd0': No such device or address
dale1@ubuntu:~$

thanks .. I'll try again later.

---

### Post by effenberg0x0 on 2011-11-16
> **ventrical said:**
> It will not detect the standard floppy but I get this when I stick in the USB floppy:


   *-scsi
          physical id: 1
          bus info: usb@3:2
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb

Ah, that makes sense... Linux sees the USB-Floppy as a USB device. I really didn't know that. So fd0 won't ever access it. You'll have to mount it as a USB, format it as a USB, use dd (tip from user Plucky right above) using a USB name, etc... Interesting.

As long as there's no other usb, and you have a floppy inside the drive, it will /dev/sdb1, etc.

---

### Post by ventrical on 2011-11-16
> **effenberg0x0 said:**
> DD is a good choice. I just don't know how / if the thing is mounting there, as USB or FD?

@Ventrical Question: Does a USB-Floppy show as a normal floppy (fd0) or as a USB device (sb0) on sudo lshw? 

One other thing: I SSHd to a machine that I know has an *internal* floppy running Maverick. In that machine, the Kernel module "floppy" is being loaded at boot in /etc/modules (was manually added). So that kernel version didn't have it by default. You probably want to check there. If it's not, sudo modprobe floppy would load it.


  Ok .. it gives me a false positive because there was absolutely no activity on the drive.

dale1@ubuntu:~$ sudo dd if=super_grub_disk_hybrid-1.98s1.iso of=/dev/sdb1
2820+0 records in
2820+0 records out
1443840 bytes (1.4 MB) copied, 0.0208696 s, 69.2 MB/s
dale1@ubuntu:~$ sudo dd if=super_grub_disk_hybrid-1.98s1.iso of=/dev/sdb0
2820+0 records in
2820+0 records out
1443840 bytes (1.4 MB) copied, 0.01882 s, 76.7 MB/s
dale1@ubuntu:~$

---

### Post by effenberg0x0 on 2011-11-16
> **ventrical said:**
> Ok .. it gives me a false positive because there was absolutely no activity on the drive.

dale1@ubuntu:~$ sudo dd if=super_grub_disk_hybrid-1.98s1.iso of=/dev/sdb1
2820+0 records in
2820+0 records out
1443840 bytes (1.4 MB) copied, 0.0208696 s, 69.2 MB/s
dale1@ubuntu:~$ sudo dd if=super_grub_disk_hybrid-1.98s1.iso of=/dev/sdb0
2820+0 records in
2820+0 records out
1443840 bytes (1.4 MB) copied, 0.01882 s, 76.7 MB/s
dale1@ubuntu:~$

Check sdb(n) is not mounted (sudo mount). If it is, sudo umount /dev/sdb(n) for every partition you find mounted..
Then, since it's a ISO, you should write it to the entire unit (sdb), not for the first partition (sdb1). So you can issue dd again, and use of (output-file) /dev/sdb. It probably will overwrite the previous attempt. dd is a power tool, but it's kind of dumb, it doesn't check much stuff.

---

### Post by ventrical on 2011-11-16
> **effenberg0x0 said:**
> Check sdb(n) is not mounted (sudo mount). If it is, sudo umount /dev/sdb(n) for every partition you find mounted..
Then, since it's a ISO, you should write it to the entire unit (sdb), not for the first partition (sdb1). So you can issue dd again, and use of (output-file) /dev/sdb. It probably will overwrite the previous attempt. dd is a power tool, but it's kind of dumb, it doesn't check much stuff.


Yepp.. that was the magic code .. just sdb (no number).

  Even though there was an input/output error  it successfully recorded the .iso to the 1.44 floppy.

 whew !!

 well .. at least I can still use Windows for some stuff .. :)

hey ... thanks again.
ale1@ubuntu:~$ sudo dd if=super_grub_disk_hybrid-1.98s1.iso of=/dev/sdb
dd: writing to `/dev/sdb': Input/output error
241+0 records in
240+0 records out
122880 bytes (123 kB) copied, 18.9921 s, 6.5 kB/s
dale1@ubuntu:~$

---

