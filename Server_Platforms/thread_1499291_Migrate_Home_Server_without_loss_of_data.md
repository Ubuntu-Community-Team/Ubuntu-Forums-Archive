---
title: "Migrate Home Server without loss of data?"
date: 2010-06-01
forum: Server Platforms
---

### Post by psychokilla on 2010-06-01
Hi, I already have a home server which has Microsoft's WHS installed and working, I have built up a large collection of media on it but I want to change to Ubuntu Server (Whatever happened to Ubuntu Home Server?). 

Will I be able to do this without losing all my media?

How do I go about using the 4TB of drive space I have on my server? Do I need to change the drives to linux or can I keep them as NTFS?

Bear in mind my WHS is installed on an automatically created 20GB partition on one of my 1TB drives.

I presume I'll be able to install gnome on the server so I can just vnc onto the server to admin it and installing samba will then allow me to access my shares with either Windows or Linux? (Why is it so difficult to add windows shares to Ubuntu?)

Lots of questions I know but...

Thanks for any assistance :)

---

### Post by arrrghhh on 2010-06-01
Well this could be tricky... The *easiest* solution would be to slap another hdd in there to run Ubuntu on.  That way you don't have to worry about it touching any of the big drives w/data on them.

Now you CAN leave the drives at NTFS.  I would highly recommend against it tho.  It will cause a ton of server overhead, plus with fragmentation and other issues with NTFS (like permissions) it would be best to migrate the drives to ext3/4 (I use 4 on my drives...)

However - you MUST be careful, if you ever want this server to run Windows again or have this physical hardware access these drives thru Windows you won't be able to.  (There are ways of accessing ext partitions in Windows, but again not recommended.)

I use webmin to manage my server - why are you installing Gnome on a server?!?

Webmin makes samba shares easy.  I don't like editing conf files unless I have to, espeically ones I only touch maybe once a year.

---

### Post by psychokilla on 2010-06-02
Thanks for the quick reply...

I only have the 4 sata ports and they're all taken with the 4 1TB drives, although I think one of them is dying a death so I may just replace it with another smaller drive which can be the ubuntu install or another 1TB drive with 2 partitions.

I presume the system drive can be at least 20GB and doesn't have to be much bigger than that, surely the smaller the better as it's a system drive too?

I also presume I can't convert an NTFS drive to ext3/4, Will I have to just copy my media/files over to a freshly formatted ext3/4 drive?

If I do format the 1TB drives as ext3/4 will they all be treated as one volume like they were with WHS or will they be treated as separate volumes? (I realise I could configure them as raid to get them to do this but that would probably just complicate matters even further and I'd be royally screwed if one died).

I'm just wondering if I could format them and give them names like Movies, TV, Music, etc?

Also what is the difference between ext3 and ext4?

Thanks again for the help

---

### Post by spynappels on 2010-06-02
Have a look at LVMs. Replace the ailing HDD and install Ubuntu on a small partition and keep the rest as LVM storage. An LVM volume can be grown as required, so you could copy enough media to free up another disk, format it to XFS (or ext3/4 but XFS is considered by some to be better for things like file servers) and then grow the LVM volume to use the new disk. Repeat this as required for all the HDDs.

---

### Post by arrrghhh on 2010-06-02
I've never used XFS, but I've heard it is good - especially if you want to span the large volumes all together - I believe LVM will help you achieve that.  I have not done it myself, not used XFS so I couldn't recommend it in good conscious :D

To answer your questions...

> **psychokilla said:**
> I presume the system drive can be at least 20GB and doesn't have to be much bigger than that, surely the smaller the better as it's a system drive too?

Yes, 20GB will be plenty.  I've crammed an Ubuntu install on a 10GB partition, and it has been kind of difficult come update time.  So 20GB should be about right - I wouldn't go lower than 15GB.

> **psychokilla said:**
> I also presume I can't convert an NTFS drive to ext3/4, Will I have to just copy my media/files over to a freshly formatted ext3/4 drive?

I would copy them.  I don't know of any utilities that claim they do it - but if any do, you'd have to take a backup of all the data anyways in case of catastrophic failure... which to me, I would just rather avoid entirely and copy stuff around to save myself the potential headache ;)

> **psychokilla said:**
> If I do format the 1TB drives as ext3/4 will they all be treated as one volume like they were with WHS or will they be treated as separate volumes?

By default, separate volumes.  If you use LVM, then yes you can have one big 'volume group' as they call it.  You should leave some free space in the group tho.  Read [this](http://www.howtoforge.com/linux_lvm) article on how to setup LVM in Linux.  The guy uses Debian Etch as his example, so the concepts are pretty much identical.


> **psychokilla said:**
> Also what is the difference between ext3 and ext4?

[Wiki article](http://en.wikipedia.org/wiki/Ext4) on ext4.  I'll just quote the first few lines...

> It was born as a series of backward compatible extensions to remove 64-bit storage limits and add other performance improvements to ext3.  However, other Linux kernel developers opposed accepting extensions to ext3 for stability reasons, and proposed to fork the source code of ext3, rename it as ext4, and do all the development there, without affecting the current ext3 users.

---

