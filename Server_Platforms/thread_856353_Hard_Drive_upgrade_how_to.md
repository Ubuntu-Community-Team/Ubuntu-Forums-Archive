---
title: "Hard Drive upgrade how to????"
date: 2008-07-11
forum: Server Platforms
---

### Post by kroon78 on 2008-07-11
Hello all

  My issue is something I think most people have/will go through with their servers.  I have a new much larger hard drive that I want to upgrade my server with.  Out with the old one, and in with this new one.

  How do I go about changing the hard drive with out losing all my data and settings.  Is there an easy way to just swap?

Thanks

Cheers

---

### Post by Titan8990 on 2008-07-11
I would backup the entire filesystem using rsync. Exclude the files /boot/grub/menu.lst and /etc/fstab. Install Ubuntu on the new drive. Boot into the Ubuntu live CD and the restore your backup.

Someone might know of an easier way but this is what I have tested and it works.

Also, I'm not sure how well this works in Linux but have you considered JBOD?

---

### Post by ixus_123 on 2008-07-11
If you just want to add space, you don't really need to get rid of the current drive.

Provided you have spare IDE / SATA channels, you can just power down the server, install the drive.

Use fdisk to format it, then mount it under something like 
/mnt/new_drive 

or in your home folder with a path like /home/yourname/movies

then you add an entry to fstab so the system can mount it at every restart

---

### Post by ixus_123 on 2008-07-11
ooops, didn't realise I was in the server section.

The same still stands but you could mount it as /var2

then copy all your data from /var on your original disk and then rename that to old-var and the new disk to var.

You'll still need to edit fstab.

If you only want one disk you could Ghost the old drive to the new one - Ghost has the option to expand partitions while copying which is pretty cool.


Ghost, will probably break grub so you'll need a boot CD to set this up again.

Other options would be DD and I'm pretty sure there are opensource versions of ghost if you google around.

---

### Post by kroon78 on 2008-07-18
Hmm, i was hoping for an easier way.  I thought for sure i was just not thinking of something.  Upgrading hard drives is very common especially in the server environment, thing is I have always just started fresh with a clean format and install.  I this situation I don't want to do that, i want to move everything over to the new drive.

---

### Post by koenn on 2008-07-18
> **kroon78 said:**
> Hmm, i was hoping for an easier way.  I thought for sure i was just not thinking of something.  Upgrading hard drives is very common especially in the server environment, thing is I have always just started fresh with a clean format and install.  I this situation I don't want to do that, i want to move everything over to the new drive.

an easier way ? Like, the drive crawls into the computer by itself, and then all files magically start jumping over to the new drive ? 

contrary to what you seem to think, people do not routinely replace system drives in servers. Adding drives for extra space is not uncommon, but actually replacing the drive where the operating system lives is not something you want to be doing on a server. If you have a raid, you might consider it. 

What you propose is possible by copying /cloning the current disk to the new one, and then swap them. You may have to edit a few files (eg /etc/fstab if it has diskUIDs) or troubleshoot grub. It doesn't get any easier than that. 

Here are some pointers: [http://users.telenet.be/mydotcom/howto/linux/disks1.htm#sysdisk](http://users.telenet.be/mydotcom/howto/linux/disks1.htm#sysdisk)

---

### Post by dorath on 2008-07-18
Recently my father purchased a larger HDD for his XP system, and wanted to move everything to that drive.  So while it's not precisely the situation you're in, it might be close enough to give you some ideas.

Defraged the old HDD, and then again for good measure.
We powered down his machine and installed the new HDD.
We then used [Clonezilla]("http://www.clonezilla.org/") to create an image of his old HDD on the new HDD.
Powered down the machine again and unplugged the old HDD, 'just in case'.
Finally we booted up with an Ubuntu 8.04 live CD and used gparted to expand his partition so that it used the entire drive.

It has been working well, and if it continues to do so for another few days we'll plug the old HDD back in and wipe it.

---

### Post by chris.zeman on 2008-07-20
Ghost For Linux is one good option.
[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

Another good option is Acronis True Image Echo Server for Linux.
[http://www.acronis.com/enterprise/products/ATISLin/](http://www.acronis.com/enterprise/products/ATISLin/)

Chris

---

### Post by windependence on 2008-07-21
Two ways both without proprietary software and both easy:

Safest way:

```
rsync -avH small_drive/* big_drive/
```

then from a bootable rescue CD:

```
grub-install
update-grub
```

Or, the fastest easiest way but could be dangerous if you switch source and target:

```
dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror
```

Where /dev/sda is your source drive and /dev/sdb is your target. DO NOT REVERSE THEM. We affectionately call dd "disk destroyer" for this reason. :)

The last method using dd is the fastest and most exact copy, just be careful.

-Tim

---

### Post by bsell on 2008-07-21
> **kroon78 said:**
> Hmm, i was hoping for an easier way.  I thought for sure i was just not thinking of something.  Upgrading hard drives is very common especially in the server environment, thing is I have always just started fresh with a clean format and install.  I this situation I don't want to do that, i want to move everything over to the new drive.

I've used Clonezilla successfully with Ubuntu. Doesn't work well with Windows (I could be doing something wrong). Your hard drive manufacturer may provide cloning software. I've successfully cloned Windows XP Home and Pro with cloning software from Seagate, Maxtor and Western Digital.

---

### Post by Titan8990 on 2008-07-21
One issue I have with these examples such as drive cloning.

Won't there be an issue with the new drive's UID being different than the old one? Won't he need to change /etc/fstab before his machine will boot properly?

My method may take longer but I believe it has the least amount of room for error. I have personally tested in many times on our server before it went into production.

---

### Post by windependence on 2008-07-22
Unless you are trying to boot from software RAID (not recommended), the UUID doesn't matter, and even if it did, dd copies the drive bit by bit so it is the most accurate copy you can get. The DOD and major crime labs all use dd because of this. 

I have literally dd'ed one SCSI drive to another, pulled it out and plugged it in to a new machine and booted with zero problems. 

-Tim

---

### Post by Titan8990 on 2008-07-22
So essentially it gives the new drive the same UID as the original?

---

### Post by windependence on 2008-07-22
It's an exact, bit by bit copy of the original drive. Try it sometime when you are just messing around. You'll be amazed. You can copy a whole drive in minutes if you use the right block size.

-Tim

---

