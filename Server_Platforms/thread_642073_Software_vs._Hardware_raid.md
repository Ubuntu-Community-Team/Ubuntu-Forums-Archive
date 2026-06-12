---
title: "Software vs. Hardware raid"
date: 2007-12-16
forum: Server Platforms
---

### Post by oni5115 on 2007-12-16
I'm curious on what the differences are between using software and hardware raid.  I know software uses more processing overhead, but I'm curious more about other things.  I've read up a bit on the different types of raid arrays, just never actually set one up yet.

Hot-swapping / drive rebuilding - I assume any raid 1 array will auto mirror itself to a new drive if I swap one,  Is this correct?  (Plan to use drive bay cages, sick of downtime and tearing cases apart when the HD  dies, and our WD drives seem to love to fail on us.)

Storage area increasing.  I've never set up a Linux box that actually had more than one hard drive, so I am wondering what would happen if I added more drives.  E.g. if I had a raid 1 array of 2 400 GB drives, and added a second raid 1 array of 500 GB drives.  Can I just expand the /home partition to be 900 GB?  Is this limited to only software raids?  Would I have to reformat Linux and reinstall it all?

Essentially, I want to build a small server that can backup all of our computers data / OS'es, multimedia, etc. that can expand if we get a lot more data.  (e.g. if we decide to say... ditch our tivo and make a multi-HD-tuner mythTV box.)

---

### Post by HermanAB on 2007-12-16
For hot swapping, you need special hardware.  A home user should not need that since replacing a drive once in 5 years isn't going to be much of a problem.  If your drives fail more often than that, then buy better drives and it will still be cheaper than special hardware.

On Linux, there is no detectable loss of performance due to software RAID.  The disk drives are so slow compared to the processor, that this is not an issue.

On a common garden variety PC, you can usually stick 2 to 4 disk drives only, so you cannot do RAID 5, but RAID 0/1 is possible.

Using RAID and logical volumes, you can expand volumes seamlessly over multiple drives, but setting it all up can be a bit of a head-ache.

Cheers,

Herman

---

### Post by jacktar on 2007-12-16
Unless I'm mistaken, the minimum spec for RAID 5 is 3 discs.

---

### Post by rsw686 on 2007-12-16
There are three kinds of RAID. Hardware RAID, hardware/software RAID, and software RAID.

Hardware RAID uses an add in card (PCI, PCI Express, PCI-X). The card has onboard memory and a processor to compute the RAID calculations. The RAID is stored in that controllers proprietary format and most likely you will need to use their drivers. The price is around $300-400 for a 4 port card. The CPU load is basically none with this setup.

Hardware/software RAID uses an add in card as well. However the card doesn't contain memory or a RAID processor. It instead off-loads the RAID calculations to the CPU. The data is still in a proprietary RAID format and you most likely need to use the card's RAID drivers. Personally I think this form of RAID is pointless unless it is used for RAID 1 or 0. These run around $100-150 for a 4 port card.

Software RAID is proprietary to the software format. In linux you can move the drive to any linux distro with the same RAID support. I've moved between Debian and Ubuntu without issue.  All the RAID calculations are performed by the CPU. However if the box is only for storage then this isn't an issue as todays processors can easy keep up.

In your situation I would go software RAID. Personally I like software RAID in all but high end corporate situations. Software RAID is more flexible with recovery and you will find lots of write-ups about mdadm. With hardware RAID you'll be contacting the manufacture for support.

You should read up on LVM as well. Since your talking about expanding your RAID down the road you'll need this to combine two RAID volumes into one logical volume.

Lets talk about setting up software RAID

If you the motherboard controller supports it you can hot swap the drive. You need to remove the drive from the array with mdadm first. Once you replace the drive you tell mdadm to add the drive back in and the rebuild will take place.

You can also convert RAID 1 into RAID 5 without loss of data with mdadm. You can even expand the RAID 5 volume to include more disks. Although a backup is always a good idea.

The basic steps are, create a partition utilizing the entire drive with the type set to linux raid. Do this for each drive. Create a raid device /dev/md0 containing those partitions.

Now create a LVM volume group and add the /dev/md0 device to it. You can divide this into many logical volumes or just one volume. Once satisfied your format with the file system of your choice.

Whats nice about LVM is down the road you can add more physical volumes, /dev/md1 for example, and expand the logical volume and file system. To the user it appears to be one device.

If you have more specific questions feel free to ask. I would recommend using VMWare first to create a test system with 5-6 drives. Look at some tutorials, practice creating the raid, adding drives, expanding the LVM, and recovering from drive failures. This way when it happens for real you will know what to do.

Linux software RAID with LVM on top is very powerful, but you must do things in the correct order and double check each command as one mistake can wipe out your data.

Some articles to read
[http://www.gagme.com/greg/linux/raid-lvm.php](http://www.gagme.com/greg/linux/raid-lvm.php)
[http://scotgate.org/?p=107](http://scotgate.org/?p=107)
[http://www.mythtv.org/wiki/index.php/LVM_on_RAID](http://www.mythtv.org/wiki/index.php/LVM_on_RAID)

---

