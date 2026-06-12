---
title: "KVM and shared directory (XP-Hardy)"
date: 2008-04-12
forum: Virtualisation
---

### Post by dukbilt on 2008-04-12
Hello everyone,

I'm using KVM to run Windows XP SP3 under Ubuntu 8.04 beta. XP works fairly well, however...

1.   I need to share a directory between XP and Ubuntu so that I can transfer files. I tried to set up Samba, but it doesn't work.I would prefer to just use a shared directory or virtual file than Samba anyway.


[INDENT]I tried sharing a virtual drive between Ubuntu and XP with

   [B]sudo mount -o loop,offset=32256 -o uid=* Share.img /media/sda8
   kvm -m 512 -hdb Share.img -localtime -cdrom /dev/cdrom -usb -usbdevice tablet -std-vga -soundhw all -net none WinXP.img[/B]

and I can see the shared drive in both Ubuntu and XP but it seems that there are two drives - changes in the drive under XP don't appear on the drive under Ubuntu.

I tried to create a floppy drive with

   **kvm -m 512 -localtime -cdrom /dev/cdrom -usb -usbdevice tablet -std-vga -soundhw all -net none WinXP.img -fda fat:floppy:/home/ewan/my_directory &**

and I end up with a floppy drive with read-only access. When I try to make it read/write with

   **kvm -m 512 -localtime -cdrom /dev/cdrom -usb -usbdevice tablet -std-vga -soundhw all -net none WinXP.img -fda fat:floppy:rw:/home/ewan/my_directory &**

I end up with an error message: 
 qemu: could not open disk image fat:floppy:rw:/home/ewan/my_directory
[/INDENT]

Any information on how to fix this?

---

### Post by tek400 on 2008-04-22
In my experience, you can't have a shared directory which is mounted on both guest and host simultaneously. I qemu-img create -f raw disk.raw 1G to create a shared 'disk'. I can run my vm with -hdb disk.raw and have it as the second disk in my vm. When the vm is shut down, then I can mount -o loop,offset.... disk.raw /local/mount/point. Then I can access the files from the VM. This will not work with the vm constantly running unless you use the monitor to disconnect/reconnect the drive. At no time can the disk.raw be accessed by two OSs simultaneously.

tek

---

### Post by tekhawk on 2008-04-30
trying this although i know about mounting loops ive never worked with the raw type image i made with qemu

here is my error

@dell-uinit-01:~$ sudo mount -o loop -t raw disk.raw /media
mount: unknown filesystem type 'raw'


without the -t raw i get a message telling me to select a filesystem so any advice would be great

---

