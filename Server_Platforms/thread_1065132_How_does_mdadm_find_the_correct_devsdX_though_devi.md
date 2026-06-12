---
title: "How does mdadm find the correct /dev/sdX though devices change between boots"
date: 2009-02-09
forum: Server Platforms
---

### Post by emaxx on 2009-02-09
As my raid6 vaporized after a few reboots, and everything was configured to the best of my knowledge, I am still brooding over the root-causes for the failure.

My idea is now:

[LIST]
[*]between boots, /dev/sd[a-g] seem to change at will. This was at least the case, when i used the system after the crash, when the raid-array was not active any more. In the system are just a few sata-disks which shall later be used for a new raid-6 configuration, but they are currently not members of a raid-array. These disks are partitioned with raid-autodetect partitions, but they are currently not in use and not in /etc/fstab. They appear after boot as /dev/sd[something] with no reproducible device-name.
[*]if this were the case in a raid6 system, i wonder how the /dev/md0 device can work: the mdadm configuration-file defines /dev/md0 explictitly to consist of e.g. /dev/sda2, /dev/sdb2 etc. I found /dev/sd[a-f]2 to be different disks after another reboot. For example, they appear suddenly as /dev/sd[b-g]2. :eek:  I ask myself, how the raid configuration can then work at all ? ](*,)
[/LIST]

To make things clearer:

First boot: 
[LIST=1]
[*]/dev/sda5  120GB operating system & home, mounted on /
[*]/dev/sdb2 1000GB unused, ID: 0xfd, shall become member of /dev/md0
[*]/dev/sdc2 1000GB unused, ID: 0xfd, shall become member of /dev/md0
[*]/dev/sdd2 1000GB unused, ID: 0xfd, shall become member of /dev/md0
[*]/dev/sde2 1000GB unused, ID: 0xfd, shall become member of /dev/md0
[*]/dev/sdf2 1000GB unused, ID: 0xfd, shall become member of /dev/md0
[*]/dev/sdg2 1000GB unused, ID: 0xfd, shall become member of /dev/md0
[/LIST]
But after another boot:

[LIST=1]
[*]/dev/sda2 1000GB unused, ID: 0xfd, shall become member of /dev/md0
[*]/dev/sdb2 1000GB unused, ID: 0xfd, shall become member of /dev/md0
[*]/dev/sdc2 1000GB unused, ID: 0xfd, shall become member of /dev/md0
[*]/dev/sdd2 1000GB unused, ID: 0xfd, shall become member of /dev/md0
[*]/dev/sde2 1000GB unused, ID: 0xfd, shall become member of /dev/md0
[*]/dev/sdf2 1000GB unused, ID: 0xfd, shall become member of /dev/md0
[*]/dev/sdg5  120GB operating system & home, mounted on /
[/LIST]

I am running intrepid, but this phenomenon (if one at all) is for sure related to other versions as well.

For the sake of completeness, my /etc/mdadm/mdadm.conf once was (before the crash):

```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid6 num-devices=5 metadata=00.90 spares=1 UUID=b0510136:1e1db6b1:fa8b810e:30df7906
   devices=/dev/sdb2,/dev/sdc2,/dev/sdd2,/dev/sde2,/dev/sdf2,/dev/sdg2

# ARRAY /dev/md0 level=raid1 num-devices=2 UUID=a8e72b94:4fed8a7b:c91d1289:ceb97d9c

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

```

---

### Post by emaxx on 2009-02-10
I have possibly found the cause of the problem, or better said: a way to avoid the problem.

The old /etc/mdadm/mdadm.conf contained this lines:
```

ARRAY /dev/md0 level=raid6 num-devices=5 metadata=00.90 spares=1 UUID=b0510136:1e1db6b1:fa8b810e:30df7906
   devices=/dev/sdb2,/dev/sdc2,/dev/sdd2,/dev/sde2,/dev/sdf2,/dev/sdg2

```

I deleted the "devices" part, so that it now looks like that:

```
ARRAY /dev/md0 level=raid6 num-devices=5 metadata=00.90 spares=1 UUID=b0510136:1e1db6b1:fa8b810e:30df7906

```

I do in fact not know, wther this is really the solution, but at least the system booted a number of times without complaints. It seems logic to me, that qualified "device" (or better said "partition")-names such as "/dev/sda2" make no sense in an mdadm-configuration file, as long as they can change at will from boot to boot.

I would anyway be happy, if someone could confirm (or negate) my conclusions, since i am not sure whether i'm on the safe side.

---

### Post by fjgaude on 2009-02-10
Okay, I can't say how your original mdadm.conf file had the device names in it, it shouldn't have such.

As I know, **md** and **mdadm** use the UUID of the disks in an array to assemble the array at boot up with a line in your fstab file that indicates where the mountpoint is.

To prove this to yourself here's the suggestion: Re-name or delete the existing mdadm.con file. Remove mdadm using apt-get, reboot. Re-install mdadm and then run this command:

```
sudo mdadm --assemble --scan
```

A new, correct mdadm.conf file is auto created, and /dev/md0 is running.

You can now add that line in your fstab to have it auto mount, after you have created a mountpoint, at boot time.

Let us know how you are doing.

---

### Post by emaxx on 2009-02-10
Thanks fjgaude,

as I'm currently rsyncing almost 1TB to the array and this job will take another 2hrs, I don't want to interrupt this work. But I'm quite sure, everthing is alright now: after I removed the device-names from mdadm.conf, my machine booted about a dozen times without any flaws: everything seems to be perfect now O:)

For the time beeing, my guess is, that the problem has been solved: the "device" settings were added by myself due to a misunderstood mdadm.conf documentation.

If any more problem arises later, i will follow your advice and return back to this thread. 

Thanks again.


BTW: is there a way to mark this thread as "solved"?

---

### Post by fjgaude on 2009-02-10
Wonderful! Make Solved by going to the top of your post and clicking on Thread Tools. In there you will find an item called "Solved".

Yes, do post if you have any troubles in the future... the reason for these forums! <smile>

A person with **ubuntu** is open and available to others, affirming of others, does not feel threatened that others are able and good, for he or she has a proper self-assurance that comes from knowing that he or she belongs in a greater whole and is diminished when others are humiliated or diminished, when others are tortured or oppressed. -- Archbishop Desmond Tutu, 1999

---

