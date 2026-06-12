---
title: "How to encrypt the system with LVM _after_ the installation?"
date: 2009-11-23
forum: Security
---

### Post by viking_maniac on 2009-11-23
With the Ubuntu/Kubuntu alternate install CD, you can very easily encrypt the whole system during install by encrypting an LVM partition.
 
But what if you install or you already have an unencrypted LVM setup that you want to encrypt to encrypt the system with preboot authorization? Are there any manuals or walk troughs for doing this? Or do anyone in here know how to?
 
Thanks in advance! :)

---

### Post by scaine on 2009-11-23
You're going to struggle to encrypt a system *after* installation.  You need a small unencrypted boot partition, then the rest of your disk is set up with a single encrypted parition, upon which you put LVM and create the various partitions you need (root, home and swap for example) according the sizes you prefer.

You can use this howto to add a Private directory to your existing install :
[http://tombuntu.com/index.php/2008/08/07/create-an-encrypted-private-directory-with-ecryptfs/](http://tombuntu.com/index.php/2008/08/07/create-an-encrypted-private-directory-with-ecryptfs/)

But in my opinion, you'd be better of with Truecrypt - it has a pretty and effective GUI and the data file it creates can subsequently be stuck on a disk and used on Macs or Windows devices.  Pretty slick.

If you really need the full disk encryption, I think you're snookered.

---

### Post by viking_maniac on 2009-11-24
> **scaine said:**
> You're going to struggle to encrypt a system *after* installation. You need a small unencrypted boot partition, then the rest of your disk is set up with a single encrypted parition, upon which you put LVM and create the various partitions you need (root, home and swap for example) according the sizes you prefer.
 
You can use this howto to add a Private directory to your existing install :
[http://tombuntu.com/index.php/2008/08/07/create-an-encrypted-private-directory-with-ecryptfs/](http://tombuntu.com/index.php/2008/08/07/create-an-encrypted-private-directory-with-ecryptfs/)
 
But in my opinion, you'd be better of with Truecrypt - it has a pretty and effective GUI and the data file it creates can subsequently be stuck on a disk and used on Macs or Windows devices. Pretty slick.
 
If you really need the full disk encryption, I think you're snookered.
 
Thanks for your reply, scaine!
 
My plan is to setup a **/boot** and a **LVM partition setup** with at least **/** during install, but _not_ encrypt it at this point with the alternate install disk.
 
The reason for doing this is so I can setup a basic unencrypted system which I can take an image of, as in complete system backup, and thereafter encrypt the LVM setup containing the system partition before I actually start to use the system as intended to.
 
I want to backup my system before it gets encrypted, in other words. Because of security reasons, you should never take a backup of an encrypted volume or file, as in cloning:
[http://www.truecrypt.org/docs/?s=volume-clones](http://www.truecrypt.org/docs/?s=volume-clones)
 
It takes a lot of time and and work to install (K)ubuntu, setup hardware, install drivers, software and setup multiple user accounts; and even set each of them up differently. If something should go wrong during all this, it's so much easier to just restore an image of the disk and continue from a backup instead of starting at square one with the alternate install CD again.
 
So everything should be in place for the encryption; all I need to do is to encrypt the LVM system partition when everything is setup just as I want it. And I want to know how to do that.
 
:)

---

### Post by Dr Small on 2009-11-24
> **viking_maniac said:**
> I want to backup my system before it gets encrypted, in other words. Because of security reasons, you should never take a backup of an encrypted volume or file, as in cloning:
[http://www.truecrypt.org/docs/?s=volume-clones](http://www.truecrypt.org/docs/?s=volume-clones)


That just depends on where you are storing the backup. After you boot, enter your LUKS password and login, the system is now decrypted and running virtually. It's not like it is still mystically encrypted. Anyone connecting over the network will see unencrypted files, which they will be able to access.

The security of the full disc encryption, is to keep your files encrypted and unreadable, while your system is off.

If you are going to the trouble to encrypt your system, then your backups should be placed on a separate drive that is encrypted also.

---

