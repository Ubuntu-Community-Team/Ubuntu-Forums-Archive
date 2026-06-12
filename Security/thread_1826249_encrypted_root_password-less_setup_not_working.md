---
title: "encrypted root password-less setup not working"
date: 2011-08-16
forum: Security
---

### Post by diversecg on 2011-08-16
I have a Ubuntu 10.04.3 server setup with dmcrypt encrypted root.  The server works fine when password is entered manually at boot, and I am attempting to setup passwordless boot utilizing a USB disk to hold the key.  I have followed instructions in /usr/share/doc/cryptsetup/README.initramfs.gz (10. The "passdev" keyscript). 

I added the key to the disk: 
cryptsetup luksAddKey /dev/md0 root.key

and added the needed information to /etc/crypttab:
md0_crypt UUID=134ec25a-f538-4ead-b3ca-4e81ae99fa4b /dev/disk/by-uuid/D7BA-BD93:/root.key luks,keyscript=/lib/cryptsetup/scripts/passdev

and then updated init without error:
update-initramfs -uv

I even tested if the key is being read properly, (returns proper key):
/lib/cryptsetup/scripts/passdev /dev/disk/by-uuid/D7BA-BD93:/root.key

At boot the system does not even appear to try the key file, boots and continues to ask for passphrase.  I did not want to remove the passphrase from the drive in case I could not boot the key (or needed to boot disks elsewhere in emergency).  There is no errors at boot and no indication in logs if the key is being tried...

I have tried the USB drive as both ext3 and fat format, no difference.  I even tried older technique that did not work ([http://wejn.org/how-to-make-passwordless-cryptsetup.html](http://wejn.org/how-to-make-passwordless-cryptsetup.html))

What am I missing?

edit: some more info it looks like the USB drive with the key is being mounted before asking for passphrase...

---

### Post by rorrison on 2011-12-27
My findings will be posted at askubuntu.com

---

