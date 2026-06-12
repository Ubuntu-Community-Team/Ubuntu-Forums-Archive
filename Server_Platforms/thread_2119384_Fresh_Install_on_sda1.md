---
title: "Fresh Install on sda1"
date: 2013-02-23
forum: Server Platforms
---

### Post by chrisguk on 2013-02-23
Im having a wee problem and Im just too scared to make a mistake because of all the media data on sda2.

I have a 2 TB disk split like the following:

sda
sda1 30GB for the OS
sda3 2.0 TB for the media
sda5 Logical swap

My OS has gone kaput and I need to reinstall the OS, what is the best step by step solution for this with Ubuntu Server 12.04?

---

### Post by darkod on 2013-02-23
When you say partition for media I assume there are no home folders inside right?

If there are, the home folders need to be used during install.

If it's only media files, you can decide not to do anything with sda3 during install. That way it will not touch the partition at all but note that it will not make a mount point too. So at start, it will not be mounted.

What you can do as the best failsafe I guess:
1. Start the server install, select manual partitioning. When the list of partition show, select sda1, hit Enter. In the submenu, select the mount point as /, use as ext4, select the format option too (to delete all existing files). When done select the option Done setting up the partition (I think it was called like that).
2. When back to the partition list, select sda5 and use it as swap area.
3. Finish the install. Boot it.
4. Once the OS is working, make the same mount point for the media partiiton (or even another one if you choose so):
sudo mkdir /mymountpoint
5. Edit the /etc/fstab to mount sda3 (or use the UUID=<string>) as /mymountpoint. Make sure to select the correct filesystem.

I guess that is the best failsafe way.

You can also select sda3 during the install and enter the mount point you want, making sure you DO NOT select the format option. That works fine. But just in case, leave it alone during install and create the mount point and fstab entry later.

PS. You will probably need to redo any permissions (and users in the OS) on the media mount point because the new OS will not know anything about your old permissions or users.

---

### Post by chrisguk on 2013-02-23
Hi,

Thanks Darko I will give that a try and report back ;)

---

### Post by chrisguk on 2013-02-23
I missed one important step so I guess thats why I was looking at the screen all confused.  I forgot to set the mount point as /.

Ive done that now and it seems to be installing with no issues.  The permissions etc are all stored on my mediawiki in case of events like this.  And that includes the fstab data though I will re check the UUID in sudo blkid.

You saved me once again so thank you for your valuable reply :)

):P):P:popcorn:

---

