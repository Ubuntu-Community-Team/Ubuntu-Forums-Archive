---
title: "encrypting root filesystem"
date: 2005-06-28
forum: Server Platforms
---

### Post by pes on 2005-06-28
Can I encrypt whole filesystem somehow in ubuntu? I found this HOWTO [https://wiki.ubuntu.com//EncryptedFilesystemHowto](https://wiki.ubuntu.com//EncryptedFilesystemHowto) but I don't understand it very much. 

I don't understand this paragraph:

"If you want to perform an upgrade to the system, just log into the "unprotected" desktop (ie reboot and press enter at the password prompt) and run the upgrade as normal. Then reboot again into failsafe mode (entering the passphrase when asked) and mount your encrypted userland to /zzz by entering the following..."

What is unprotected desktop and why I have to run some veird cript everytime I upgrade?

I also found this gentoo HOWTO [http://forums.gentoo.org/viewtopic.php?t=191052](http://forums.gentoo.org/viewtopic.php?t=191052)

It looks much smarter, bud will it work with ubuntu? Please help.... I think it's good idea to encrypt everything, just for the case somebody steal my laptop. I'm sure there should be some good HOWTO and be supported.

---

### Post by pes on 2005-07-01
OK. Now I have encryption working. I've used the first HOWTO but I didn't create the /zzz partition. I know I will be unable to boot when password is lost.

I've used this commands:

#create encrypted partition
sudo cryptsetup -y create cryptedusr /dev/hda6
#create filesystem
sudo mkfs.reiserfs /dev/mapper/cryptedusr
#mount
mount /dev/mapper/cryptedusr /mnt
#copy all stuff to new crypted partition
cp --preserve=all -r /var /usr
cp --preserve=all -r /home /usr
rm -rf /usr/tmp
cp --preserve=all -r /tmp /usr
cd /usr/var
rm -rf tmp
ln -s ../tmp ./tmp
cd /
rm -rf /var
rm -rf /home
rm -rf /tmp
ln -s /usr/tmp /tmp
ln -s /usr/var /var
ln -s /usr/home /home
cp --preserve=all -r /usr/* /mnt
rm -rf /usr
mkdir /usr

and modified my /etc/fstab:

/dev/mapper/cryptedusr /usr     reiserfs defaults       0       1

and /etc/crypttab:

cryptedusr /dev/hda6

now everything works ok, but partitions aren't correctly unmounted on shutdown. It shows these messages:

Deactivating swap:
umount: none busy...
Unmounting local filesystems:
umount: none busy remounted read-only
Stopping crypto disks: crypteduser(busy) Unable to unlink device node...

Probably some problem with opened files in /usr? But I'm lost, please help

---

### Post by heitor_capovilla on 2006-01-20
HOWTO: Ubuntu 5.10 (Breezy Badger) with encrypted Root, Home and Swap
[http://ubuntuforums.org/showthread.php?t=120097]("http://ubuntuforums.org/showthread.php?t=120097")

---

