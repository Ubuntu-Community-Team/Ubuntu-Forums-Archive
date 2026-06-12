---
title: "Boot USB disk corrupt"
date: 2018-06-29
forum: Server Platforms
---

### Post by 4integration on 2018-06-29
Hi,

I have a HP Home Server Gen8 with Ubuntu Server 16.04.4 LTS with GRUB2 installed on a separate USB stick.

Now the USB stick have been corrupt so need to take another USB and reinstall GRUB2.

How can I do that?

---

### Post by oldfred on 2018-06-29
BIOS or UEFI?

If BIOS and server is still running:
       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo parted -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb 
sudo update-grub

If not running, you need to boot something. You could use Boot-Repair and use it to install grub to flash drive. Or use Supergrub to boot server & install grub to flash drive.

      
 [URL="https://help.ubuntu.com/community/Boot-Repair"]https://help.ubuntu.com/community/Boot-Repair

[https://www.supergrubdisk.org/rescatux/](https://www.supergrubdisk.org/rescatux/)
[/URL]

---

### Post by 4integration on 2018-06-29
I pretty sure it is BIOS.
[https://1drv.ms/u/s!AnjEso9HHQJWuD1_jtcF4KPoNNB0]("https://1drv.ms/u/s!AnjEso9HHQJWuD1_jtcF4KPoNNB0")

Server is not running - I have tried boot-repair in Ubuntu Live CD but it complains that it is running in legay mode
[IMG]https://1drv.ms/u/s!AnjEso9HHQJWuDyghEpzd56S65jm[/IMG]
[https://1drv.ms/u/s!AnjEso9HHQJWuDyghEpzd56S65jm]("https://1drv.ms/u/s!AnjEso9HHQJWuDyghEpzd56S65jm")

Supergrub - I could not make that to boot for some reason

---

### Post by oldfred on 2018-06-29
Now we really have to know if actual install is UEFI or BIOS.

And the message from Boot-Repair is saying you booted it in UEFI mode, but it seems to know you want BIOS/CSM/Legacy?

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by 4integration on 2018-06-29
Hmmm, correct.
It seems that it is booting Ubuntu Live CD in UEFI mode

[http://paste.ubuntu.com/p/wjbsfxb8Nk/](http://paste.ubuntu.com/p/wjbsfxb8Nk/)

I have followed the guide here to install the server and have the same HW setup
[https://blog.linuxserver.io/2015/03/24/setting-up-a-linux-home-server-using-the-hp-proliant-microserver-gen8-g1610t-3/](https://blog.linuxserver.io/2015/03/24/setting-up-a-linux-home-server-using-the-hp-proliant-microserver-gen8-g1610t-3/)
Especially section "Selecting the right boot disk".

---

### Post by oldfred on 2018-06-29
Moving to server sub-forum.
I really do not know servers, but it does not look like you have LVM, RAID or any server specific configurations.

You show grub installed to sdg, if you select that in your BIOS, does it not boot?

You have some drives as gpt and some with the older MBR(msdos) configuration.
It looks like you are booting from sdg, which is BIOS/MBR configuration even though newer hardware that can boot in UEFI mode.
And sda & sdc are USB drives.
Plugging & unplugging USB drive and rebooting will change drive order. So before running any command that uses /dev/sdX as device, run fdisk or parted to make sure you have correct drive for sdX. Or your sdg may not always be sdg.

You also have a lot of partitions as ext3 which is unusual since Ubuntu converted to ext4 as default  back in 2009 or 2010.

Do not run any auto-fix from Boot-Repair. It tries to install grub to every drive which is not necessary. And it will error on the gpt drives as to install grub in BIOS boot mode on a gpt drive you must have a tiny 1 or 2 MB unformatted partition with bios_grub flag.

Only run Boot-Repair's advanced mode and choose sdg (or whatever it is) and that MBR for repairs, if you need to update grub.

---

### Post by 4integration on 2018-06-30
Thanks for info.
The server setup is that in the 4 SATA bays I have storage only disks and a SSD in DVD slot where Ubuntu is installed. That DVD slot cannot boot in AHCI mode and therefore using an USB stick internal on motherboard which can boot.

So I enabled SATA Legacy support in BIOS instead of default AHCI - and removed all disks except for SSD with Ubuntu and booted that but entered "emergency mode". Logged in as root.
Plugged in the USB stick and executed as you proposed:
sudo grub-install /dev/sdc
sudo update-grub

Shutdown, changed back to AHCI mode in BIOS and plugged in the disks. Now it boots from usb but still entering emergency mode.

Hmmmm...

---

### Post by oldfred on 2018-06-30
You may be able to do a full uninstall/reinstall of grub.
If you can boot, you can do that from inside Ubuntu.
Or use Boot-Repair, or chroot into system.

---

