---
title: "Need some advice for my LVM"
date: 2008-05-30
forum: Server Platforms
---

### Post by Jordanwb on 2008-05-30
I have two 40GB hard drives. When I was installing 8.04 Server onto this computer and got to the partition screen I selected "Set Up LVM" (or whatever). So to figure out what I needed to do I did this at the prompt:

jordanwb@Server:~$sudo lvm
lvm>help

and went through each command. However in TorrentFlux, Saidar etc. it reports the drive as being 38 GB instead of 76 GB despite vgdisplay shows the drive as being 76 GB. So I obviously didn't do something right. Either that or the packages failed horribly.

I found this thread where someone couldn't find any documentation: [http://ubuntuforums.org/showthread.php?t=286991](http://ubuntuforums.org/showthread.php?t=286991)

But I'm confused regarding this part:

> Work with your FIRST / Booting drive (ie the /dev/hda drive)
Create a real /(root) partition and select the filesystem time you prefer. Make sure to mark this as Bootable and to set the mount point to / .

Now use the same process to create a swap partition -- set it to 4Gb as you want. In the details page for the partition you need to select filesystem type "swap" and ignore the mountpoint.

Then select the FREE SPACE on the same drive and add another partition. This time, for the filesystem type, select "Physical volume for LVM" (or something similar).

Do I make the ext3 partiton 36 GB and the lvm partion 1 GB or the other way around? (My computer has only 256 MB of hard ram)

[Edit]

I typed pvdisplay to view the physical drives. I think I did mess something up because it lists one drive as /dev/sda5 and the other as /dev/sdb1. Shouldn't they both be 5?

---

### Post by Jordanwb on 2008-06-05
Hello?

---

### Post by Jordanwb on 2008-06-05
I'm getting a replacement computer for my server from my tech teacher at school.

I cleaned off a 250GB hard drive which I want to use. I also have 2 40GB hard drives. I want to have as much space as possible. Of course I realize that there's a swap partition needed too. So let's say the drives are listed like so:

/dev/hda -> 250GB (has 250059350016 bytes total)
/dev/hdb -> 40GB (has 41110142976 bytes total)
/dev/hdc -> 40GB (has 41110142976 bytes total)

In my current LVM setup which has only the 2 40GB drives one hard drive (which has LVM working correctly, the other I don't think does), has a 256 MB ext3 partition, and the rest is for LVM (according to Gparted). There is no real swap partition because it's a LVM group, I want to have the swap as a real partition, if possible.

I've searched for documentation on how to set up an LVM, and I found very little.

What I'm looking for how to set up the partition structures for the three drives mentioned above so that my LVM gets the maximum amount of space possible.

---

### Post by mojoman on 2008-06-06
Have a look at this, it worked wonders for me.

[http://tldp.org/HOWTO/LVM-HOWTO/index.html]("http://tldp.org/HOWTO/LVM-HOWTO/index.html")

As for swap, I think that has to be on a primary partition but I might be wrong. 

/mojoman

---

### Post by Jordanwb on 2008-06-08
I've printed out some pages off of that. I looked at some mainly adding a physical volume, and it left me scratching my head. So I I typed --help alot to show the available sumcommands. Plus by using a spare disk and the fdisk command I was able to figure out how to make a partition a certain file structure (like Linux LVM, or Linux SWAP, etc...)

---

