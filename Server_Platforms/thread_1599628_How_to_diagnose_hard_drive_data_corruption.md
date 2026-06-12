---
title: "How to diagnose hard drive data corruption"
date: 2010-10-18
forum: Server Platforms
---

### Post by jpalermo on 2010-10-18
I'm running 10.04.  I've got two drives in a software RAID 1 configuration with mdadm.

I've long suspected some sort of data corruption was happening, as fsck frequently required my attention when I would force it every few weeks.

This was confirmed when I was downloading a ~7 GB torrent using rtorrent.  Chunks of the completed file would hash fine, and then it would finish, and do the hash again, and completed chunks would be bad.  This happened several times in a row.

As far as I can tell, smartctl reports everything is fine on both disks.

I remember doing a memory check ~6 months ago, and that didn't come up with anything.

Is there any other troubleshooting I can do to diagnose where the problem might be?

---

### Post by rouben on 2010-10-18
I wouldn't assume your disk(s) are/is bad based on torrent hashes being bad. Sometimes torrent downloads do go badly, and this is legitimate.

I would suggest looking for disk errors in the output of dmesg. Here's an article that may come in handy:
[http://www-01.ibm.com/support/docview.wss?uid=swg21387697]("http://www-01.ibm.com/support/docview.wss?uid=swg21387697")

---

### Post by jpalermo on 2010-10-18
After I started getting the bad torrent chunks (or more accurately, chunks I already had started going bad) I copied everything to another box and it never had another bad chunk.

I've seen mild corruption in the past too.  Jpeg files that are bad, but if I look in a backup, they used to be good.  And the rather common fsck problems.

dmesg didn't show any errors, and I've never spotted any errors in the syslog in the past.  Everything seems to be telling me it is working correctly, but I end up with corrupted data sometimes.  I'm not sure if the data corruption is happening though.  It seems like it's not a read only corruption problem, because it is repeatable when I find it.  I'm just not sure if it is in the drive, the controller, the memory, or a software bug (I am using a software RAID 1 config).

---

### Post by James78 on 2010-10-18
Well, if fsck reports nothing, then that's the first thing to guess that the drive is fine. Second thing is to check the drives SMART status if you can, as those reports can be very useful. And as that also appears to be good.. Did you check the MDADM monitoring? Because you can check each disk and have it be fine, but it's usually also a good idea to check the RAID as a whole, e.g. /dev/md0

---

### Post by jpalermo on 2010-10-19
fsck does report errors at a higher level than I would expect.  Most of them are not unexpected, working under the assumption that some data corruption is happening somewhere.

mdadm has never reported any problems.  I've got it running the monitor daemon, and it's never spit out an error.

I'm not sure if that helps to diagnose the problem or not.  If the data corruption were happening in the OS before it gets written to disk, the mirrors would be identical.  If it is happening on one or both of the disks, the mirrored array should not be identical.

But I'm not sure what sort of checking mdadm does, I would assume it doesn't do two reads and compare them.  And there doesn't seem to be any option for checking consistency in a mirrored array.  So perhaps it just works on faith, and doesn't help diagnose the problem.

I suppose it might be possible to boot to a live cd, and mount both drives instead of the array, and then somehow compare the contents of them.  Not sure what could be used to do that though, or if that is even a wise idea.

---

### Post by James78 on 2010-10-19
Maybe we could try a little troubleshooting. If you take the drives out, plop them in another computer, download something, and it works. Then it must be something in the other computer.

> I suppose it might be possible to boot to a live cd, and mount both drives instead of the array, and then somehow compare the contents of them. Not sure what could be used to do that though, or if that is even a wise idea.
In fact you should always do that (without the mounting part). It's is never advisable to scan the disk when it's mounted, as this will usually cause false positives, and even then, it could damage the filesystem permanently. Trying to fix the disk while it's mounted is even worse. That's why it's recommended to have all disks that are being checked unmounted. Of course, e2fsck already displays that error as a warning if it's mounted anyways.

---

### Post by jpalermo on 2010-10-20
That's a good idea.  They are the system partition for the machine they are in currently, but it didn't occur to me that I could mount them as a secondary partition in another box.

I'll give that a shot, and see if they still have corruption.  That way I won't have to break the mirror set either.

---

### Post by jpalermo on 2010-10-21
Ok, so in a separate machine, the array does not have corruption problems at all.

I'm going to run a memory check once I can get a live cd into the original machine.

Assuming the memory checks out, that only leaves software and the motherboard (unless I'm missing something).

Software seems unlikely as the other machine is running the same Ubuntu revision.

Any other suggestions?  Or is a bad motherboard the most likely culprit?

---

### Post by James78 on 2010-10-21
Correct. If it's not the hard drive, then the last things it can likely be are the RAM, the software/kernel, or the motherboard. The most likely culprits would be software/kernel first, RAM, then motherboard. It's probably likely not the RAM or motherboard either, and probably software related somehow. Reinstalling may fix it. Or reinstalling some packages may fix it. But I don't know how to find a package that's misbehaving without any much more detailed information than this, so finding the culprit package could be very hard.

As for the motherboard part, it could also be the network connection. For example, the wifi card (if you have one). If it's the ethernet adapter, that'd be harder to "replace" because it's built into the motherboard (and for all we know it's not the adapter itself, but how the motherboard software handles the adapter).

Either way, good luck!

---

### Post by jpalermo on 2010-10-31
So the memory test came back fine.

I've put the drives back into the original computer, and now I'm unable to reproduce the corruption problem.  My first thought was that it was related to the cables, but it sounds like SATA transfers always do checksums, so it shouldn't be possible to get corruption between the controller and the drive.

I did resync the array when it was in the other computer.  I can't see how that would change anything though.  This is really the only thing that has changed between taking the drives out and putting them back in.

When I first put them back into the original machine, I tried them on different SATA ports, but after I put them back on the original ones, I'm still unable to get the corruption problem back.

The only thing I can think of is that there is a bad SATA port, but right now I'm reading data from the other drive in the mirror set, so I'm not seeing it.  Not sure if that is how RAID1 does it, or if it reads from both drives (which would leave me with no possible explanation).  If there were a way to verify consistency in a mirror set, that could possibly provide some good info, but I can't seem to find any option like that.

---

