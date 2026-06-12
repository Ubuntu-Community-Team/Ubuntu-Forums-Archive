---
title: "[IDEA] Nervous Nelly Backup/Update/Restore"
date: 2009-03-18
forum: Ubuntu Brainstorm
---

### Post by jamesdcarroll on 2009-03-18
I'll be honest, when it comes to updating my system I'm a nervous nelly.  I spend the entire time chewing my fingernails and praying that the progress bar keeps moving and I don't lose everything in a blink of the screen. Here's my idea, I know its a bit 'ambitious':

During the upgrade process, give the user the user the option to backup their system such that it can be restored if something goes wrong. Yes, they probably should've done it before starting, but make it easy for them and really walk them through it.  Then (and here's the ambitious part) let then upload it to an Ubuntu server under the condition that it will only be there for like a day or so (give them a user name/password, etc to make it secure).  Then if something goes horribly wrong, they can re install fresh and do a "Restore from Ubuntu Repository" and get back to where they were.

I know there are huge holes all over the place in that idea, but I'm just throwing it out there for thought. For me personally, like I mentioned, updating from one version to another is just the most gut wrenching thing.

Thanks!!

---

### Post by smartboyathome on 2009-03-18
Canonical would not be able to afford he upload bandwidth cost for this.

---

### Post by Therion on 2009-03-18
> **jamesdcarroll said:**
> ... like I mentioned, updating from one version to another is just the most gut wrenching thing.
It will be for the first half-dozen or so times you do it.  After that, cakewalk.  Seriously.  

You'll know you're "over it" when you start doing fresh installs out of boredom.

---

### Post by jflaker on 2009-03-18
> **Therion said:**
> It will be for the first half-dozen or so times you do it.  After that, cakewalk.  Seriously.  

You'll know you're "over it" when you start doing fresh installs out of boredom.

Been there, DONE THAT!  :lolflag::lolflag::lolflag:

---

### Post by Merk42 on 2009-03-21
Oh this isn't a proposed name and feature for 11.04?

Seriously though if you're so worried about information being lost, create a separate /home partition.
I usually don't upgrade anyway since the servers are so slow the day of release.  I get the torrent, burn the disc and do a fresh install.
Speaking of slow servers, it's bad enough downloading the updates when everyone else is, could you imagine how slow it would be when people are **uploading** too?

---

### Post by jamesdcarroll on 2009-03-24
I'd love to but when I moved from Windows to Ubuntu I dual booted my system for a while to make sure I liked ubuntu, etc and now I think my partitions are all screwy. One physical drive is all ext3 and given that its has used area on it I have to believe that's where everything is. The other drive has two NTFS partitions, one of which is flagged as 'boot'. I'd love to clean them out, but (being the nervous nelly that I am) I'm afraid to lose everything.

This has been a bane of mine for some time as I've cleaned those drives of everything that I want and would love to format them to ext3 and be done with all things Windows (except my little VirtualBox one; not giving up MSMoney ;) ), but its that 'boot' flag I can't just get past. I expect to reboot my machine and have it say 'Boot whatever not found. Frying hard drive, notifying wife, have a nice day'

---

### Post by Merk42 on 2009-03-24
Ideally how do you want your setup to be?
I'm currently dual booting Ubuntu 8.10 and Windows 7

Ubuntu can read NTFS and Windows can (with a download) read EXT3, although it seems your Windows needs are filled with Virtualbox, which is fine.

Just show me, and anyone else reading the thread, how your drives are set up right now.
```
sudo fdisk -l
```

Or load up GParted if you prefer a more graphical approach.

---

### Post by jamesdcarroll on 2009-03-24
My ideal setup would be one that is pure Ubuntu/ext3 so that I can say that there's no more legacy Windows stuff.  Not that it matters that much, but I'd like it to be "clean". More importantly I'd really like to have what's been mentioned above: the ability to have a dedicated 'home' partition (or conversely/preferred a dedicated system partition) so that I can install/update/kill some time with as good a feeling as possible that I won't lose, at least, my stuff. Here's the result of the command:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35f535f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19574   157228123+   7  HPFS/NTFS
/dev/sda2           19575       30401    86967877+   f  W95 Ext'd (LBA)
/dev/sda5           19575       30401    86967846    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4046d95f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38346   308014213+  83  Linux
/dev/sdb2           38347       38913     4554427+   5  Extended
/dev/sdb5           38347       38913     4554396   82  Linux swap / Solaris

```

The only piece of information that GPartEd has that I don't see there is 'MOUNTPOINT:

```
dev/sdb1 = /
dev/sda1 = media/disk10
dev/sda5 = media/disk11
``` 

Disk10 and disk11 show up in FileExplorer as such.  And one last piece of info that you may find helpful. Its the pieces of /boot/grub/menu.lst that seem to be relavant (at least to me):

```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=73d8d030-f086-43a1-b8b5-ef616d9169db ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic 

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
# Title		Microsoft Windows 2000 Advanced Server
# root		(hd0,0)
# savedefault
# makeactive
# chainloader	+1
```

I hope that helps and if there's anything else you need please let me know. If I can FINALLY get this squared away I'll be doin' that little dance that makes my wife say, "Dude, stop it... you're creeping me out"


Thanks again

---

### Post by Merk42 on 2009-03-25
What sort of files are in that first HDD? The one with all the NTFS formatted things?
If you don't need any of that, you could just format the whole thing and do a fresh install onto that.
My root partition is only about 16GB and I've only used a little over 4GB.

---

### Post by jamesdcarroll on 2009-03-25
There's nothing on it except files that for some reason Ubuntu won't let me delete. If I format it and install fresh there could/should/would I delete the install on the other drive?  Would grub "automagically" find it the new one and ignore the old?

I was playing with Synaptic and saw "Save Markings" and saved it with the 'Save full state' flag flipped on.  Got something like this

```
xserver-xorg		install
popularity-contest		install
x11-apps		install
libmono-addins-gui0.2-cil		install
libchipcard-libgwenhywfar47-plugins		install
mii-diag		install
libopenal1		install
bluez-gnome		install
libstdc++6-4.3-dev		install
```


Would that allow me in the fresh install to Read the Markings back into the fresh install and have synaptic download/install those packages?

---

### Post by Merk42 on 2009-03-26
If you do a fresh install it will "automagically" find the new install.  It may however also find the old one, but most likely default to the new.

I'm not sure about that second question, but worst case scenario, it doesn't install them, you come back to this very thread, and there's your list of packages to install.

---

### Post by mrsteveman1 on 2009-03-26
There is actually a REALLY good solution to this problem that another OS has solved completely, in the future Ubuntu might be able to implement something similar once btrfs or grub2 are in common use.

[Unbreakable upgrades, ZFS and apt-get]("http://tech.xerces.com/unbreakable-upgrades-zfs-and-apt-get.geek")

---

