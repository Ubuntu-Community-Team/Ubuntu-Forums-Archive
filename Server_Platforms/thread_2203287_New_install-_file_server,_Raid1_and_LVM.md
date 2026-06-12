---
title: "New install- file server, Raid1 and LVM"
date: 2014-02-02
forum: Server Platforms
---

### Post by david_hammond on 2014-02-02
I've set up an old PC running ubuntyu 12.04 as a samba server using the default partition table. 

We've a new dell server arriving this week, with 2x 2TB hd's. 

The plan is to run raid1 configuration, from reading online i'm confident setting up the raid.

I'm struggling to find how to set up lvm over raid, as it may be neccassary to add additional drives later in time to expand the storage capacity.

What would be the preferred partitioning of the HDD, root and boot on smaller partitions, with home on its own larger one?

---

### Post by ally2 on 2014-02-02
Hey there I am trying to do exactly the same as you :)

the software raid side is easy 

[http://www.youtube.com/watch?v=vQtUBp5aad8](http://www.youtube.com/watch?v=vQtUBp5aad8)

As for the LVM that's what I'm trying to work out how to put LVM over raid do you configure LVM first or the raid first?

I found this earlier haven't had a chance to go through it may be useful though 

[http://blog.miketoscano.com/?p=307](http://blog.miketoscano.com/?p=307)

---

### Post by david_hammond on 2014-02-02
A little more reading I think i've got in my head how it works.

I assume set raid1 up first to mirror the drive, then set the lvm up.

I don't think I need to set up partitions just use the whole disk for lvm, and set up the required volumes. 

I'm not sure if you need to do this on both drives in the raid like with conventional partitions? 

I'll view your links thanks!

---

### Post by ally2 on 2014-02-02
If you do get something working document it and get it up in here lol ive been looking at this for a few hours and am getting nothing but headaches :)

I have read that you do not necessarily need to have LVM to reszie partitions, Raid onto of LVM can be a pain in the a__ 
someone suggested that if you ever needed to re-size a partition you can fire up Gparted and re-size to your needs.

---

### Post by steeldriver on 2014-02-02
Yes basically you would set up the soft RAID and then add that /dev/md*N* device as the physical volume (PV) to your LVM volume group (VG) out of which you carve the logical volumes (LVs)

I've done it once - really just as a learning experience - on my home HTPC, but I don't really know enough to guide you further (or even to comment on whether it's a good way to go - it doesn't necessarily make adding disks any easier)

---

### Post by ally2 on 2014-02-02
How do you do this during a text install? Say you had two drives of equal size, Firstly what would be the best way partition the drives in terms of layout for a Raid1 config. 

Secondly during the text install how do you add the LVM on top and what would be a good layout of volumes for a basic server setup? 

Once I get this down I'm going to document it because the documentation out there seriously is lacking

---

### Post by david_hammond on 2014-02-04
In my haste, and after watching too many video's of installing a standard RAID1, without LVM, I just steamed ahead and did that. It was only after it had finished installing I realised. :(

I'll have an experiment with out test server when I get chance.

---

