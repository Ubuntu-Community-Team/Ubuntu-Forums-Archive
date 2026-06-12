---
title: "Possible to create a raid 5 array with only specified system drives?"
date: 2009-12-14
forum: Server Platforms
---

### Post by tstack77 on 2009-12-14
I am looking to build both a raid5 NAS and HTPC all-in-one. In total my system will house 5 1TB green drives, with 4 of the drives storing all the family memories in raid5, and the 5th used primarily for the OS and movies for the HTPC.

Is it even possible to set this up, or am I better off spending the few hundred dollars more for 2 dedicated systems?

---

### Post by Krupski on 2009-12-15
> **tstack77 said:**
> I am looking to build both a raid5 NAS and HTPC all-in-one. In total my system will house 5 1TB green drives, with 4 of the drives storing all the family memories in raid5, and the 5th used primarily for the OS and movies for the HTPC.

Is it even possible to set this up, or am I better off spending the few hundred dollars more for 2 dedicated systems?

Yes it's possible (and easy) to setup what you want.

Assuming that you are going to use MDADM for your RAID array, all you do is create the array with the drives you wish to use.

Here's an EXAMPLE ([COLOR="Red"]**don't type in the following... it's just an example**[/COLOR]):

```

sudo mdadm -C /dev/md0 -n 4 -l 5 /dev/sda /dev/sdb /dev/sdc /dec/sdd

```


This assumes that your 5 hard drives are '/dev/sda' thru '/dev/sde'.

The command means:

-C = "create" (a RAID array)
-n = "number of drives to use"
-l = "RAID level (i.e. RAID 5)"

The list of /dev/sda through /dev/sdd means "use those 4 drives to create a RAID 5 array called "/dev/md0". Note that we didn't use the drive '/dev/sde' (the fifth drive) and you can use it for anything else you like.

If MDADM was already installed on your computer, you may have a config file '/etc/mdadm/mdadm.conf'. Look at it and see if there's anything entered for the ARRAY section.

If not, you can generate it like this (AFTER your RAID array is made):

```

sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf

```


If MDADM isn't installed yet, obviously you have to do this:

```

sudo apt-get install mdadm

```


Lastly, realize that when you create a RAID array, any data that was on the drives will be lost. Also, it will take some time for a new array to build and sync itself (you'll see the hard drive light on for a few hours!).

Watch the progress of the array build like this:

```

sudo cat /proc/mdstat

```

Also, after the RAID array (/dev/md0) is created, you will have to enter it in your /etc/fstab file and mount it somewhere.

And of course, the RAID "drive" must be formatted before it can be used.


Hope this helps...

-- Roger

---

### Post by Krupski on 2009-12-15
> **tstack77 said:**
> I am looking to build both a raid5 NAS and HTPC all-in-one.

Why separate drives?

I built a network storage drive just like you want to build (and I use it for the same thing... as a file server to put movies on the TV and also to backup the home PC).

I put the OS (Ubuntu Linux 9.04 Server 64 bit) on a 4 GB Compact Flash card.

Then there are 4 hard drives (2 TB each) setup as a RAID-5 array.

The system boots and runs from the Compact Flash card... the hard drives are strictly data storage... there isn't one byte of Linux on them (operating system-wise I mean).

Consider building your box that way.

By using a compact flash card as a separate "drive" for the OS, you can also simply use "dd" to make an image backup of the OS any time you like. This makes it easy to revert to a "last known good" version if you screw up a configuration or upgrade.

The compact flash is also more rugged and reliable than a hard drive... obviously... no moving parts and low power too.

Give it some thought.

-- Roger

---

