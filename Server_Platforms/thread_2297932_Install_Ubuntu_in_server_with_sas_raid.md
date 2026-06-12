---
title: "Install Ubuntu in server with sas raid"
date: 2015-10-07
forum: Server Platforms
---

### Post by Julio_MGM on 2015-10-07
Hello everyone.
I am new to ubuntu.

I have installed it on computers an all is good.
I am now trying to install it on a server and I am stuck.

from the driver manufacter a have to :
 
> 1. Copy "aacraid.ko" to a floppy disk or USB flash.

2. Start installing Ubuntu 14.04.1 Server Linux by booting from the installation CD select Install Ubuntu Server,
   Press CTRL+ALT+F2 to switch to console2 while Ubuntu detects the network.

3. Insert your USB key or floppy disk

4. Run parted_devices command (scan for device, assume if USB drive is assigned to /dev/sda1)

5. Type the following commands:
    # mkdir /mnt2  /AACRAID
    # mount /dev/sda1 /mnt2
    # cp -R /mnt2/* /AACRAID 
    # umount /mnt2

6. *** Please remove the USB flash before the insmod command ***

7. # modprobe -r aacraid
   # cp -f /AACRAID/aacraid.ko /lib/modules/3.13.0-32-generic/kernel/drivers/scsi/aacraid/aacraid.ko
   # insmod /lib/modules/3.13.0-32-generic/kernel/drivers/scsi/aacraid/aacraid.ko

8. Press CTRL+ALT+F1 to return to installer. Continue the installation as usual. !!! READ STEP 9 NOW !!!

9. Do not reboot after the installation is complete. Press CTRL+ALT+F2 to
   switch to console 2 again.

10. Type the following commands:
    # cp -f /AACRAID/aacraid.ko /target/lib/modules/3.13.0-32-generic/kernel/drivers/scsi/aacraid/aacraid.ko
    # chroot /target
    # /sbin/depmod -a 3.13.0-32-generic
    # update-initramfs -u -v
    # exit

11. Press CTRL+ALT+F1 to return to the installer. Reboot to complete the installation.

but when i run the parted_devices i get

> /dev/sdf   15938355200


and when i try to mount with
> mount /dev/sdf /mnt2

i get

> mount: mounting /dev/sdf on mnt2 failed: Invalid argument

Can anyone help please.

Thanks

---

### Post by darkod on 2015-10-08
You are trying to mount the whole stick instead of a partition. You need to mount the partition where you copied the files you need.
Notice the difference in their instructions (/dev/sda1) and your command (/dev/sdf). The number specifies the partition to mount. You need to use like /dev/sdf1 if that's where the files are.

---

