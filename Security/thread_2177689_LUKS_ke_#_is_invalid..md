---
title: "LUKS ke***** # is invalid."
date: 2013-09-29
forum: Security
---

### Post by PhillyKingston on 2013-09-29
My system seemed to have crashed, when it rebooted I was unable to mount an encrypted drive I have.  I have tried the password to no avail, and looking online trying to figure out the problem I found a few things.  

kris@Desktop:~$ sudo cryptsetup -v isLuks /dev/sdf
[sudo] password for kris: 
LUKS ke***** 4 is invalid.
LUKS ke***** 5 is invalid.
Command failed with code 22: LUKS ke***** 5 is invalid.

kris@Desktop:~$ sudo blkid -p /dev/sdf
/dev/sdf: UUID="9938889b-0d0e-4c07-87c9-ba0fce8bcfdf" VERSION="1" TYPE="crypto_LUKS" USAGE="crypto" PTTYPE="dos" 

From what I read (in older threads elsewhere) only 0 or 1 should really be used, so I am not sure why I can't load the drive and ignore the problems with the other ke*****s.  Though I guess it might have changed.  I was hoping someone here might be able to help point me in a direction that will allow me to recover the data.

---

### Post by sandyd on 2013-10-01
> **PhillyKingston said:**
> My system seemed to have crashed, when it rebooted I was unable to mount an encrypted drive I have.  I have tried the password to no avail, and looking online trying to figure out the problem I found a few things.  

kris@Desktop:~$ sudo cryptsetup -v isLuks /dev/sdf
[sudo] password for kris: 
LUKS ke***** 4 is invalid.
LUKS ke***** 5 is invalid.
Command failed with code 22: LUKS ke***** 5 is invalid.

kris@Desktop:~$ sudo blkid -p /dev/sdf
/dev/sdf: UUID="9938889b-0d0e-4c07-87c9-ba0fce8bcfdf" VERSION="1" TYPE="crypto_LUKS" USAGE="crypto" PTTYPE="dos" 

From what I read (in older threads elsewhere) only 0 or 1 should really be used, so I am not sure why I can't load the drive and ignore the problems with the other ke*****s.  Though I guess it might have changed.  I was hoping someone here might be able to help point me in a direction that will allow me to recover the data.
See if
[http://code.google.com/p/cryptsetup/wiki/FrequentlyAskedQuestions#4._Troubleshooting](http://code.google.com/p/cryptsetup/wiki/FrequentlyAskedQuestions#4._Troubleshooting)
helps

---

### Post by BluegrassHero on 2013-10-01
Can you find the disk in /dev/disk/by-uuid ?

I mount mine like this:

cryptsetup luksOpen /dev/disk/by-uuid/YOUR-UUID-STRING mydisk
(prompts for password to decrypt)
mount /dev/mapper/mydisk /mymountpoint

---

### Post by PhillyKingston on 2013-10-01
> **sandyd said:**
> See if
[http://code.google.com/p/cryptsetup/wiki/FrequentlyAskedQuestions#4._Troubleshooting](http://code.google.com/p/cryptsetup/wiki/FrequentlyAskedQuestions#4._Troubleshooting)
helps

It was the first place I looked.  They refer me to the "Backup and Data Recovery" section.  Which tells me how to back up the header, which I can't do because of the error.  I am working on getting a new HDD to backup the entire partition.  It talks about recovering a mapped partition, which I can't because the system rebooted.And by then I am pretty much out of recovery options.  Unless I missed something.

> **BluegrassHero said:**
> Can you find the disk in /dev/disk/by-uuid ?

I mount mine like this:

cryptsetup luksOpen /dev/disk/by-uuid/YOUR-UUID-STRING mydisk
(prompts for password to decrypt)
mount /dev/mapper/mydisk /mymountpoint

When I tried that I get the following:

kris@Desktop:~$ sudo cryptsetup luksOpen /dev/disk/by-uuid/9938889b-0d0e-4c07-87c9-ba0fce8bcfdf mydisk
LUKS ke***** 4 is invalid.
LUKS ke***** 5 is invalid.

Basically I can't seem to proceed with those slots in this state.  I am not sure if there is anything I can do to ignore the state of those slots that might allow me to proceed.

---

### Post by PhillyKingston on 2013-10-12
HDD arrive, so I backed up with dd_resuce to be safe to the new drive.

Most of what I read recommended using the newest version of cryptsetup (at this time it was 1.6.1) which is not included with Ubuntu.  I wasn't able to compile the code when I downloaded it from the site so I got a copy of the Fedora 19 Live and booted the system.

I ran "cryptsetup repair" on the disk directly.  It fixed the invalid ke*****s and I was able to enter the passphrase on the drive.  I am in the process of copying off the data now as I suspect the drive is failing which lead to the issue in the first place.  I hope this helps some folks.

As an aside, I wasn't sure what the passphrase was initially (having used a different one on drives as I added them, but you can see all your encrypted HDD passphrases in the "Passwords & Keys".

---

