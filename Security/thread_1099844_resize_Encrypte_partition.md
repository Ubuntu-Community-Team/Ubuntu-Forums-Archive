---
title: "resize Encrypte partition"
date: 2009-03-18
forum: Security
---

### Post by nick937 on 2009-03-18
I am following everything listed here:
[https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)

but I get stuck at this:

```

cryptsetup luksOpen /dev/sda5 crypt1
Enter LUKS passphrase: 
Command failed: No key available with this passphrase.

```

I know the password is correct because I can still decrypt it when I boot up off of my hard drive. I must be missing something (an extra setting or something)?

---

### Post by bodhi.zazen on 2009-03-18
did you run that command with sudo ?

---

### Post by nick937 on 2009-03-18
yes, I used sudo.. ](*,)

---

### Post by nick937 on 2009-03-19
if no one can help me with this, can someone put me in the direction of a good tutorial for setting up LVM/Encryption install for ubuntu manually? I would like to dualboot windows with Ibex(encrypted install)

---

### Post by hyper_ch on 2009-03-19
I've written LVM/Encryption howto for Debian Lenny... because 8.04 and 8.10 still have problems with random keys for swap.

Did you modprobe dm-crypt?

---

### Post by nick937 on 2009-03-19
> **hyper_ch said:**
> I've written LVM/Encryption howto for Debian Lenny... because 8.04 and 8.10 still have problems with random keys for swap.

Did you modprobe dm-crypt?

yep

---

### Post by hyper_ch on 2009-03-20
did you modprobe aes?

---

### Post by nick937 on 2009-03-21
no I didnt modprobe aes, it didnt show it on the site.. do I do it after I modprobe dm-crypt ?

---

### Post by hyper_ch on 2009-03-21
doesn't matter when you modprobe it ;)

just do it before you try to unlock the encrypted drive.

---

### Post by nick937 on 2009-03-21
ok ill give it it a try in a little bit :popcorn:

---

### Post by nick937 on 2009-03-21
didnt work.. this is what happened:

```

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo apt-get install lvm2 cryptsetup
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  cryptsetup lvm2
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 464kB of archives.
After this operation, 1454kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com intrepid/main cryptsetup 2:1.0.6-6ubuntu2 [105kB]
Get:2 http://archive.ubuntu.com intrepid/main lvm2 2.02.39-0ubuntu2 [359kB]
Fetched 464kB in 1s (301kB/s)
Selecting previously deselected package cryptsetup.
(Reading database ... 102335 files and directories currently installed.)
Unpacking cryptsetup (from .../cryptsetup_2%3a1.0.6-6ubuntu2_i386.deb) ...
Selecting previously deselected package lvm2.
Unpacking lvm2 (from .../lvm2_2.02.39-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up cryptsetup (2:1.0.6-6ubuntu2) ...
update-initramfs is disabled since running on a live CD

Setting up lvm2 (2.02.39-0ubuntu2) ...
Backing up any LVM2 metadata that may exist...done.
update-initramfs is disabled since running on a live CD

ubuntu@ubuntu:~$ sudo modprobe dm-crypt
ubuntu@ubuntu:~$ sudo modprobe aes
WARNING: Error inserting padlock_aes (/lib/modules/2.6.27-7-generic/kernel/drivers/crypto/padlock-aes.ko): No such device
ubuntu@ubuntu:~$ sudo modprobe aes
WARNING: Error inserting padlock_aes (/lib/modules/2.6.27-7-generic/kernel/drivers/crypto/padlock-aes.ko): No such device
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/sda5 crypt1
Enter LUKS passphrase: 
Command failed: No key available with this passphrase.

ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/sda5 crypt1
Enter LUKS passphrase: 
Command failed: No key available with this passphrase.

ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/sda5 crypt1
Enter LUKS passphrase: 
Command failed: No key available with this passphrase.

ubuntu@ubuntu:~$ 

```

---

### Post by hyper_ch on 2009-03-21
well, aes doesn't exist anymore... it changed....

try aes_x86 if you're 32bit or aes_x86_64 if you're 64bit. Also load dm_crypt and dm_mod and aes_generic

---

### Post by nick937 on 2009-03-22
I finally got it to  work, but I had trouble while I was formatting my partitions.. so I gave up and just reinstalled and instead of using the guided setup with LVM and encryption, I did a manual set up... Now I am having trouble with my windows xp install disc... it gets frozen after it says "checking system"... maybe one day I will get it all working!;)

---

### Post by hyper_ch on 2009-03-23
hmmm.... no clue about windows... but it might be the partitions got now mixed up.

Post the output of

```

sudo fdisk -l

```

```

cat /boot/grub/menu.lst

```

---

