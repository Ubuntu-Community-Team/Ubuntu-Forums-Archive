---
title: "Filer Server Additional Harddrives in Raid 1 for /Data"
date: 2008-11-24
forum: Server Platforms
---

### Post by sam702 on 2008-11-24
Hello Ubuntu Server Gurus,

I know "search" is my friend.  But because I'm a noob to Ubuntu Ibex and Linux in general, I don't know how to properly phrase the questions for the answer.

So here is my situation...

I have an Ibex 8.10 AMD64 Server running with Samba on a Raid 1 setup.  I have two (2) physical 300G sata harddrives, and through the Ubuntu installation I accepted the raid setup.  My setup is primarily for a file server.  I made 3 partitions on the Raid 1 for the root, swap, and home directories.  I can network and share files with my other window platforms with proper permissions and users setup.  This is a headless file server, and it is quite nice so far.  Thank you Ubuntu and Samba!

Now here is what I would like to do...

Install 2 more physical harddrives, set it to Raid 1, make 3 partitions and mounted them to /projects, /archives, and /administration, respectively.  These are locations where all data are stored/shared.  These are the directories that I will regularly back-up to an external USB drive.

I installed mdadm with the sudo apt-install mdadm.  I made a gparted live CD.  I installed the two (3) physical drives.

Questions-

Where and when do I use gparted, mdadm, and what are the line commands?

Please include step-by-step and command syntax.

Also, if you do sent script or conf files, please send them in txt format so I can use windows to read them at this time.  I am slowly weening away from windows:)

Thank you much.

---

### Post by fjgaude on 2008-11-25
It would be better for you to learn all the things necessary to handle what you wish to do... but here's how to get started:

While booted into Ubuntu do all these things:

```
sudo fdisk -l
```

That will show the names of the drives you have in your system.

Now using **gparted** partition each drive identically into the three pieces you wish.

Now use **mdadm** to make three arrays:

```
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
```

assuming the first partition is called /sdb1 and /sdc1

Then add filesystem to the array:

```
sudo mkfs -t ext3 /dev/md0
```

You can use the **watch** command to watch the array build:

```
sudo watch cat /proc/mdstat
```

Make a mountpoint for the array:

```
sudo mkdir /projects
```

Now do all this for the other two partitions.

Let us know how you are doing.

---

### Post by sam702 on 2008-11-25
FJGAUDE-

Thank you for your reply.  I did some preliminary RAID 1 build based on your information and it seems to work out good.

I'm going through a series of test right now.  What I will be using is a RAID 1 for the boot and root directories.  Then I will us 2 RAID 5 setups for the data directory.  The RAID 1 will be 2 physical 300G harddrives, with two partitions for the root and the home directory.  The first RAID 5 will have 3 physical drives, with 1 partition for high I/O output file transfer.  The second RAID 5 will also have 3 physical drives but with 3 partitions.  Both of the RAID 5 will have LVM overlay to accommodate future expansion.  I don't need the LVM for the RAID 1, because that is not going to be expanded.

I'm testing and simulating failure and rebuilding process to verified the system before deploying it.

Also, what do you think about using the Hardy Heron 64-bit server for a fileserver compared to the Ibex version?  I like the Heron because of the extended support to 2013.  What is your take on this?  

Thanks.

---

### Post by fjgaude on 2008-11-25
I never use LVM... as a reliable server I guess I'd go with the 8.04.

Booting from raid1 will require having full grub, MBRs on both drives. There are HOW-TOs around showing how to do that. I never boot from a raid, especailly software raid. Too complicated. If hardware or software fails I use another drive that's ready to go for boot up.

Let us know how you are doing.

---

### Post by sam702 on 2008-11-25
FJGAUDE-

Thanks for the quick reply.

What you are saying is...

1.  Have one (1) physical drive with GRUB, Boot, and root directories located there.
2.  Have three (3) physical drives for RAID 5 for the file share directories.
3.  Both #1 and #2 are not on LVM.
4.  Have another drive ready to go in case #1 fail.
5.  Use 8.04.1 for reliability.
6.  All is based on software raid.

Is this correct?

Right now I have...

1.  Have two (2) physical drive on RAID 1 with GRUB, Boot, and root directories located there.
2.  Have three (3) physical drives for RAID 5 for the file share directories.
3.  Only #2 are is on LVM.
4.  Using 8.10 (Ibex)
5.  All is based on software raid.

My goal is to create a headless fileserver using Samba to interface with windows platforms.  No applications will be running from the fileserver, only for file serving.  Reliability, stability, robust, and speed (RAID 5) for file I/O are my goals.

Should I go with no RAID for #1, and have a another drive ready to go or continue with the #1 on RAID 1?

Thanks.

---

### Post by fjgaude on 2008-11-25
Well, the only issue with booting from software raid1 is if one drive fails we have to make sure that we can still boot.

Yes, raid5 is great for speed and reliability.

> 1. Have one (1) physical drive with GRUB, Boot, and root directories located there.
2. Have three (3) physical drives for RAID 5 for the file share directories.
3. Both #1 and #2 are not on LVM.
4. Have another drive ready to go in case #1 fail.
5. Use 8.04.1 for reliability.
6. All is based on software raid.

Is this correct?

Yes, but gee, I can't tell you what to do. My requirements are different from yours. I always backup all important data, one is online, another near-line, and the last is off-line. All depends on how important it is in never losing any data, period.

---

