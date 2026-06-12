---
title: "Home NAS encryption: encrypt root or not?"
date: 2015-01-13
forum: Server Platforms
---

### Post by darkod on 2015-01-13
Hi all,

I have a small basic home NAS on a HP Microserver with Ubuntu Server 14.04 LTS. To cut a long story short: I will be upgrading it with two more HDDs and I got the idea to encrypt the data. Right now I have 2 HDDs with /dev/md0 raid1 for root and /dev/md1 raid1 for data.

I was thinking leaving root unencrypted and only encrypt the big data partition after I add the new storage. Main reason is that the server is headless and I would prefer not complicating root with encryption. Since I don't want to set up automatic decryption, I would need to involve busybox, etc to enter password manually for root to unlock and continue booting. If anything gets messed up, I need to take it to another room and connect KVM on it.

On root I do not have any important data and I do not plan to leave the LUKS key file or passphrase anywhere in root or /home. The server is a simple NAS with basic samba, minidlna and transmission for ocassional downloading.

Would I be making huge error not encrypting root? My main goal is to protect the data with the encryption.

I appreciate any comments. Thanks.

---

### Post by MAFoElffen on 2015-01-13
darkod! Long time...

IMHO-- On a home server, what do you really have in s sys volume that is senstive? Win Server doesn't care. But then again, they haven't figure out how to boot an encrypted volume either...

I agree that BSD mentality is a little too open, That mentality is that if you don't have physical security of your server, then you have bigger problems to resolve. But on BSD, anyone with physical access can change a root password. <-- too open!

If you encrypt the volumes you have sensitive data on... If you have a system problem, you can work on getting it going no effort. 

If you encrypt the boot volume (easy to do) and have system problems... where are you at then? Just have a good backup... (Image the system volume.)

Just my thoughts...

---

### Post by mastablasta on 2015-01-14
> **darkod said:**
> 

Would I be making huge error not encrypting root? My main goal is to protect the data with the encryption.


why ? what is your recovery plan? 

usually in these forums people have issue recovering encrpyted files. i am not saying you can't do it. but if something goes wrong (eg part of disk gets corrupted or something like that) you might loose it all, not just one file.

> **MAFoElffen said:**
> 
I agree that BSD mentality is a little too open, That mentality is that if you don't have physical security of your server, then you have bigger problems to resolve. But on BSD, anyone with physical access can change a root password. <-- too open!

physical access is access. you can reset password for root user (admin) on ubuntu as well if you have physical access. [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

in fact if you have physical access and want to access unencrypted data all you need is a live USB/DVD. ofcourse with UEFI you might not be able to easilly boot those withouth UEFI password.

---

### Post by darkod on 2015-01-14
Recovery plan from what? Disaster or forgotten passphrase? The disaster recovery would be same as if there is no encryption, it doesn't change much. And the passphrase I won't forget, plus I will have a key file too.

The main idea is to protect the data if someone steals the whole unit or just the disks. Precisely because they can reset passwords of unencrypted data and get access to the OS. With the encryption of my data (I don't care much about the OS and few config files), at least I am making it more difficult and in many cases not worth trying to decrypt it. Rarely who would bother with that. We are not talking about industrial espionage. :)

---

### Post by TheFu on 2015-01-14
If you want to protect the data, have 100% know-you-can-recover backups.
If you want to hide the data when it is at rest, use encryption.  In my mind, if you don't encrypt the entire drive, then encryption is worthless. Anyone who wants access to the data will be patient. They will install a keylogger into the boot kernel and wait.  Of course, if you are trying to protect the data from a little brother (not a government), almost any kind of encryption will be sufficient.

Have you encrypted any areas of a partition before, then logged in with a different userid and looked at the data yet?  Do that before you decide. It is all there, unencrypted after being mounted with only file permissions to help. Anyone with root will have access after a mount.

OTOH, in case there are any lurkers .... IMHO, any device that can be easily moved must be encrypted as much as possible. USB disks, smartphones, netbooks, laptops - encrypt.

Oh - and on Linux if you have physical access, you can change the root (or any local) password too ... unless there is boot-level encryption.  Then it is just a little harder. There are complex attacks against whole drive encryption under Linux. They've been demonstrated at DefCon.

---

### Post by MAFoElffen on 2015-01-14
> **darkod said:**
> Recovery plan from what?
Same as I inferred... If you backup an encrypted volume, not the same as an image of. (non-encrypted/encrypted)

If a system volume goes south and you have an image of that volume, no problems, you restore the disk image of that disk and go on your way. 

Should not be a challenge for you... Still have the same job as a Sys Admin? *** Most here answering you probably do not remember your many posts here (previously, a few years ago...) and the times you diligently spent helping others Recover from their RAID disasters. (I remember.) This is not your first adventure.

I know you and that you have enough mdadm experience. Do what I do. RAID1 on sys volumes. Build RAID1 with 3 disks. Remove 1 disk from the array. Pull that disk and keep as a sys backup. Sys volumes don't take up much room. 3 times the chance of getting back up and going.

---

### Post by darkod on 2015-01-14
Thanks for all opinions. Lets clear some things further...

I am aware no code is unbreakable, especially for BB. I don't care about that, I have nothing to hide. My main goal is for example if a burglar grabs the Microserver under his arm or pulls the disks out, that they can't read them easily and look into personal documents, photos, etc. To make it hard enough so that in most cases they would "only" format the disks and reuse them...

Again, we are never 100% safe but I am rather confident I do not need to worry about keyloggers, viruses, trojans, etc for getting the luks passphrase. In fact, the way I plan to set it up there will be no passphrase typing so nothing to log...

Here is how I plan to set it up and why I prefer unencrypted root so I can simply log in and work on it regardless the data partitions.

I will install new disks and configure LVM so I can join the old disks too in one continuos space after I copy the data. The new disks are 3TB vs old 2TB so I can copy all easily, and then add the 2TB to the LVM. I'm not going into too much details for the LVM because that's easy to set up.

Now comes the interesting part, and since this is my first venture in encryption I wanted your opinion.

First starting with luksFormat of the LVM device e.g. /dev/vg/lvdata. I will select a good strong passphrase which takes slot 0. I want a passphrase because I want to be sure I can always reach the data what ever happens with the luks key file.
Then I will create luks key file using my ubuntu desktop, creating it directly onto a usb stick with small partition for that purpose. Most tutorials recommend creating a random 4KB file. I will do the luksAddKey --key-file (takes slot 1).
There will be no mapping in /etc/crypttab. It will be done manually on boot/reboot.
In /etc/fstab I will create an entry for the usb partition by UUID and for the luks data mapping, both with noauto option (so it doesn't try auto mount).
Create a basic bash script and put it in rc.local. The script will do the usb mount, and luks unlocking and mapping. Something like:
```
mount /mnt/usb
luksOpen --key-file=/mnt/usb/keyfile
mount /dev/mapper/luksmapping
umount /mnt/usb
```

If it works as I imagine it, it should unlock the encrypted data partition only when the usb is plugged in during power on or reboot. If there is no usb, the server will boot the OS but the data is not unlocked nor mounted, so any shares etc using it will also not work. Correct me if I'm wrong...

There is no passphrase keying and the passphrase or key file will never be on the server, in the root partition, or in /home... As I mentioned I will even create the key file on another machine.

I think that should be enough for "simple" anti-theft data protection. This is not for a backup solution, that's another topic.

Comments???

---

### Post by MAFoElffen on 2015-01-15
Comment--

I haven't done an encrypted boot myself, so just thinking on that. Not exactly sure were the encryption process starts. I know Grub has some modules and switches for encryption... Guess I'm going to have to venture into that to see how that actually works, when and where.

On all mine, there is no formal /dev/usb... As a device type. A usb key (or any USB storage device- thumbdrive, disk, etc.) will come up as a /dev/sdx, where x is the last in the order after your internal disks. Verify that, by boot and mounting it. So taht would be something like /dev/sdm1/keyfile... The problem with that is that if you add a drive, pull a drive or a drive drops out of the array, then the drive ID of the USB device changes. I run into the same problem setting a custom Grub Menu Option to boot from internal USB... That I sometime had to change that drive assignment to adjust for that... I started that by just using device ID...

To get around that, I set it up using the UUID for the mount of the USB key in the fstab. That points to a specific UUID of the filesystem in a volume. A dd copys over the UUID of the file system to spare USB keys... (USB Keys do sometimes fail.) Seems to be a lot more flexible, because it does not depend on the drive order. If removed, then fails. 

Then you just use the fstab mount point in your script to point to what is on it...

---

