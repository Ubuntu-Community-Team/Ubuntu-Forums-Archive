---
title: "update-initramfs =&gt; target sda7_crypt uses a key file, skipped"
date: 2009-02-11
forum: Security
---

### Post by DjNDB on 2009-02-11
Hello,

I had to copy my system to another Hard Disk, because my / partition was too small. My System is encrypted using LUKS via dm-crypt.

Before I copied my system I was able to use a keyfile in /etc/crypttab. The keyfile was on the encrypted root partition and was used to decrypt the /home partition.

After copying this doesn't work anymore. 

My crypttab looks like this, UUIDS replaced by censored[123]:
# root
sda6_crypt /dev/disk/by-uuid/censored1 none luks
# swap
sda5_crypt /dev/disk/by-uuid/censored2 none luks,swap
# home
sda7_crypt /dev/disk/by-uuid/censored3 /root/keyfile luks

when i run 
sudo update-initramfs -u 
it says
cryptsetup: WARNING: target sda7_crypt uses a key file, skipped

It works however when i use
sda7_crypt /dev/disk/by-uuid/censored3 none luks

I had this problem earlier when i installed the System the first time, when i thought i could use the keyfile for swap. This however is the home partition.

Before copying it worked just fine with a similar crypttab, except for the UUIDS of course.

Please someone help. I find it so annoying because now I even have to Enter 3 Passwords on boot for decryption instead of just 2.

$ uname -a
Linux localhost 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid

---

### Post by hyper_ch on 2009-02-11
what do you worry about it? first the root partition gets unlocked, then the key is available to unlock the other partitions. You don't need (and don't want) the key to be stored in your initrd.

---

### Post by DjNDB on 2009-02-11
> **hyper_ch said:**
> what do you worry about it? first the root partition gets unlocked, then the key is available to unlock the other partitions. You don't need (and don't want) the key to be stored in your initrd.

Thank you for your advice. It let me take a deeper look and I found out what the problem was.

The Migration caused some device name changes, and I found the most locations I had to manually adapt.

The Problem here was, that my system wanted to resume from my home partition instead of swap.

There was a message "resume: could not stat the resume device file '/dev/mapper/sda7_crypt'" in the terminal.

I had to set the correct device in two files:
/etc/initramfs-tools/conf.d/resume
/etc/uswsusp.conf

After that my system worked as before and "update-initramfs" did not produce the error message anymore.

---

