---
title: "Using 1 password to encrypt 2 drives Ubuntu 9.04 RC"
date: 2009-04-18
forum: Security
---

### Post by macromorgan on 2009-04-18
I'm playing around in a VM trying to see if what I want to do is feasable, and I'm doing it with Ubuntu 9.04 RC in preparation for its impending release.

Basically, I've got 2 physical drives in a computer.  On my test machine running in Virtual Box this is signified by 2 virtual HDs, and on my production machine it will be a netbook with 2 physical drives. One drive in the production machine will be a 4 gig SSD (will be an unencrypted /boot and an encrypted / partition) and the other will be a 16 gig permanently mounted USB flash drive that's soldered onto the motherboard directly (will be an encrypted /home).

On my test machine I have installed Ubuntu 9.04 RC using the alternate installer and partitioned the drives correctly.  /dev/sda1 is the /boot partition, /dev/sda2 is the physical volume for encryption for my / partition, and /dev/sdb1 is the physical volume for encryption for my /home partition.  As soon as I reboot after the initial install I'm prompted for my / password and then the drive mounts successfully, and then I am prompted for my /home password and the drive mounts successfully.  Is there any way to only have it prompt me for my / password only and auto mount the /home partition?

I've tried editing the /etc/crypttab file but to no avail.  For the /home entry I've tried changing the word none to "password" with quotes, and I've tried changing it to /etc/password where /etc/password was a file with nothing more than my password in it.  Any other thoughts on how I can encrypt /home without having it prompt for a password?  I'd strongly prefer to do it this way versus using the encrypt /home mumbo jumbo that is an install time option since 8.10.

Thank you.

edit:  Nevermind; I figured it out myself.  After I couldn't get the partition to mount I created a keyfile from /dev/urandom and then used the cryptsetup luksAddKey command to create a second password for the partition using the keyfile I generated.  I then referenced the keyfile in /etc/crypttab and it works just fine now.  Yay.

---

