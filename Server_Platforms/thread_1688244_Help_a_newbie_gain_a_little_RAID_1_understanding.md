---
title: "Help a newbie gain a little RAID 1 understanding"
date: 2011-02-15
forum: Server Platforms
---

### Post by frotzed on 2011-02-15
So I installed 10.10 on a RAID 1 array for the first time in my life last night.  I've tested the RAID by shutting down, pulling plugs on one HDD and booting.  It all works fine.  I have two questions, however, because I just want to make sure certain behaviors are normal.

1) As I said, I installed 10.10 last night.  This morning I checked to make sure both drives were up and active.  I then installed some applications from the software center.  Then, I noticed that the drives were out of sync with regards to data, so the RAID was rebuilding.  Is it normal behavior for a RAID 1?

2) I was pouring through my Disk Manager and noticed that each individual HDD has 3 partitions: (RAID component)(Extended)(Swap).  So it seems that each drive has one partition that is part of the RAID but then the Swap partitions are not part of the RAID.

I then looked at the md0 and that volume has no partitions, it only has a RAID component.  Is this normal?  Or, should the md0 have a partition for RAID content and then a partition for Swap?

Thank you in advance.

EDIT: I've installed software RAID.

---

### Post by frotzed on 2011-02-17
bump

---

### Post by SeijiSensei on 2011-02-17
> **frotzed said:**
> I noticed that the drives were out of sync with regards to data, so the RAID was rebuilding.  Is it normal behavior for a RAID 1?

Not really.  If it happens repeatedly, it probably means one of the drives is becoming unreliable, especially if it's the same drive being rebuilt each time.  If it continues, I'd consider replacing the drive.

> So it seems that each drive has one partition that is part of the RAID but then the Swap partitions are not part of the RAID.

Yes.  Since swap is essentially just a bitbucket, it's usually not stored on top of a RAID array.  If both drives have a swap partition, take a look at /etc/fstab.  Are there two entries marked for swap, indicating both partitions are in use, or just one?  If the latter, you can add the second partition manually if you'd like.  However I'd run the command "top" first to see how much swap you're using now.  You may have plenty already.

> I then looked at the md0 and that volume has no partitions, it only has a RAID component.  Is this normal?  Or, should the md0 have a partition for RAID content and then a partition for Swap?

Yes, it's normal.  RAID creates "devices" in *nix-speak, onto which filesystems are installed.  From the point of view of Linux, there isn't anything different between the partition /dev/sda1 and the RAID device /dev/md0.  

You could use fdisk to mark the swap partitions as type "fd" (Linux RAID) rather than type "82" (Linux swap), then use mdadm to make a second RAID device that you could format with mkswap and mount as a single swap device.  As I said before, this is really uncommon.  Just mount one or both partitions as swap, and you'll be fine.

---

### Post by frotzed on 2011-02-17
Thank you so much for the reply.  What you said about Swap makes perfect sense.  

Regarding one drive being faulty, both drives are literally 4 days old, bought at the same time.  I know that doesn't mean they're both without fault, but I'm saying that probability is low on my list.

I'm going to try the install again, this time paying extra attention to the way swap is configured, and then doing a bit more with the RAID after it's up and running.

-- On a side note, when I install Windows 7 in a fake RAID (using the BIOS to configure the RAID array before the OS touches it) the RAID doesn't seem to give any indication of constant rebuilding, judging by what I can see from the Intel Rapid Storage application. --

---

### Post by Stephann on 2011-02-17
RAID arrays can be build on partitions.  The raid device, then, becomes a 'device' to the kernel; you install directly onto that device, just like you would with, say, sda3.

In my experience, I *rarely* have need for swap space, given that I always have overkill on RAM.  *nix systems don't use nearly as much swap space as Windows systems; I'd just park one swap partition on one of the drives, and the equivalent space on the other drive I'd do something more useful with (like install a 4 gig 'backup' installation, so I don't need to boot from a live cd to perform maintenance or backups..)

Odds are your raid array had to be rebuilt because you yanked one of the drives out.  Rebuilding takes a long time (as the entire drive has to be rebuilt.)

---

### Post by SeijiSensei on 2011-02-17
> **frotzed said:**
> Regarding one drive being faulty, both drives are literally 4 days old, bought at the same time.  I know that doesn't mean they're both without fault, but I'm saying that probability is low on my list.

I would only start to worry if the rebuilding happens frequently.

Another possible, though unlikely, problem is if the machine didn't shutdown properly.  Loss of power would force a rebuild of the array, for instance.  Make sure you always shutdown from the menus.  If you're using the command line, you cah shutdown by running "sudo shutdown -h now" and turning off the machine when it has completed its tasks, or running "sudo shutdown -r now" and turning off the machine when it reboots.

---

### Post by YesWeCan on 2011-02-17
> **SeijiSensei said:**
> I would only start to worry if the rebuilding happens frequently.

Another possible, though unlikely, problem is if the machine didn't shutdown properly.  Loss of power would force a rebuild of the array, for instance.  Make sure you always shutdown from the menus.  If you're using the command line, you cah shutdown by running "sudo shutdown -h now" and turning off the machine when it has completed its tasks, or running "sudo shutdown -r now" and turning off the machine when it reboots.
I noticed that once. Why is this?
ext4 uses journalling. I assumed this was a method to recover from an unexpected power fail or other disk write interruption. Why does the raid need to be rebuilt? Is this something to do with physical sectors being out of sync?

---

### Post by YesWeCan on 2011-02-17
@frotzed

Would you take a look at System/Admin/Disk Utility and click on each disk in turn and check the SMART status? This should report any disk errors that may be occurring. Normally it shows a green circle and says "Disk is healthy".

---

### Post by gmargo on 2011-02-17
How often do you see the RAID 1 rebuilding?  I haven't used software RAID for a while, but I recollect that there was a cron job that ran once a week (or month?) that caused a rebuild.

---

### Post by frotzed on 2011-02-17
@YesWeCan: In the disk manager both individual drives are healthy.

@Stephann: Your explanation of how the Kernel views the RAID as it's own separate device helped me wrap my brain around this, thank you!  I also think you may be right in that I was probably a bit impatient when I pulled the plugs to test the RAID and then plugged them back in.  Since I'm dealing with two 1TB drives, I'm sure the rebuild process should take 4+ hours.

@SeijiSensei: I think you're right.  I'll give it a few weeks and if the rebuilding occurs very frequently I think I'll have room to worry. 

@Everyone: I appreciate you sticking with me on this.

---

### Post by Stephann on 2011-02-17
Don't be surprised if it takes longer; it'll rebuild when it does :)

That said, regarding your comment about the journal.  The RAID is independent of your filesystem's journal.  A RAID isn't like a filesystem driver; mdadm doesn't 'see' ext3 or ntfs.  It sees data from a direct access view; sort of like a record player has no clue if it's playing rock, jazz, or polka.  All the software knows is that bit 0x231fa2 at offset 210245213842 on drive A doesn't match bit 0x3114a2 on the same offset on drive B, so there must be something out of whack, lets rebuild.

Shutting the power down on a RAID is never a good idea.

Warm wishes

---

### Post by YesWeCan on 2011-02-18
> **frotzed said:**
> @YesWeCan: In the disk manager both individual drives are healthy.
That would suggest your brand new disks are ok. :) At least in terms of data storage.

If the RAID resyncs again, without being due to pulling plugs, you have a serious issue that you need to deal with. Eg: I have experienced problems with badly fitting sata cables in the past causing intermittent connectiins. Rsyncing is due to some sort of failure.

---

### Post by YesWeCan on 2011-02-18
> **Stephann said:**
> Don't be surprised if it takes longer; it'll rebuild when it does :)

That said, regarding your comment about the journal.  The RAID is independent of your filesystem's journal.  A RAID isn't like a filesystem driver; mdadm doesn't 'see' ext3 or ntfs.  It sees data from a direct access view; sort of like a record player has no clue if it's playing rock, jazz, or polka.  All the software knows is that bit 0x231fa2 at offset 210245213842 on drive A doesn't match bit 0x3114a2 on the same offset on drive B, so there must be something out of whack, lets rebuild.

Shutting the power down on a RAID is never a good idea.

Warm wishes

I wonder how mdadm knows that there are inconsistent bits? On power on it does not check the whole array. I wonder whether mdadm checks the kernel records to see whether the kernel had to repair the filesystem and then rebuilds affected disk?
Another question arises as to how many disks can be failed in this way after a power cut? I mean, without RAID you can sleep well at night knowing that a power cut will not affect your filesystem integrity thanks to journalling. But if you are using RAID, as a means to improve data security, is  there a real risk that a power cut could cost you part or all of your array?

---

### Post by Stephann on 2011-02-18
Briefly, a journaled file system does not equal complete protection from data loss in the event of a power cut; it just reduces the likelihood (ask any mac user.)  That said, the probability of either partial or complete filesystem loss on RAID1 due to power loss is very, very low.  When we mention data loss due to power failure, the odds are good that you'll simply lose whatever data was about to be written.  Suppose you're downloading a 4 gig iso image of the latest version of Ubuntu.  Power loss would potentially corrupt that particular image, since there's a read/write operation taking place on that file, but that isn't going to damage the integrity of your entire filesystem.

That said, you should always back your data up; RAID helps prevent data loss, but it is *not* a backup solution.  If you accidentally delete your /sbin directory, that directory will be deleted from both drives.  If a new distribution upgrade breaks something vital to your work flow, that upgrade has taken place on both drives, simultaneously.  If one file becomes corrupt, that corruption will extend to both drives.  If the machine gets stolen, RAID won't help protect your data loss.

A backup solution means taking snapshots of your existing files, in good and working order, to a storage medium that isn't attached to your machine.  Given that Terabyte drives are running as little as $50, there's no reason not to make use of it, and *nix systems have amazing free solutions for backing up and staying backed up.  If you have questions on that topic, let us know :)

Warm Regards.

---

### Post by frotzed on 2011-02-18
OK, the software RAID 1 finished syncing and in Disk Utility it says both individual disks are healthy.  However, for one disk it says "There are a few bad sectors" but it does say the disk is still "healthy."  Is this normal?

Another question, since I do have a spare drive, would it be more stable for me to install the OS and Home directory on the spare drive and then create a RAID 1 array for storage?

---

### Post by Stephann on 2011-02-18
Sometimes new drives do have a couple of bad sectors, which could be the culprit for your RAID rebuild.  This is especially true of SSD drives.  Mind you, when I say a 'couple' it could mean up to a couple hundred.  Run the SMART extended drive scan, it'll try to find it's own bad drives, and take a few hours in the process.

As for performance, you actually have increased performance and reliability on a RAID1.  That means quicker boot times, quicker program loading, etc.  Don't sweat it.  Use your spare drive for a backup, in the case something really goes haywire.

---

### Post by frotzed on 2011-02-18
Thanks Stephann, I'm feeling pretty comfortable now, with all this new information.

---

### Post by YesWeCan on 2011-02-19
I agree with Stephann. If it works don't mess with it. But keep an eye out for resyncing. It should never do this unprovoked unless there is a problem you need to address.

---

### Post by frotzed on 2011-02-20
I'm honestly not trying to drag on this thread unnecessarily, but one of my good friends (who's been working with computers far longer than I) has told me that software RAID is unstable when compared to fake RAID.  Is there any credence to this statement?

---

### Post by SeijiSensei on 2011-02-20
I have machines that have run Linux software RAID for years without problems.  One of them runs RAID5 and provides mail services for 200 users.  Mail is pretty disk-intensive compared to many server tasks except for heavy database access.  Does your friend have any actual experience on which he based this comment, or is he repeating a rumor he heard online?

---

### Post by frotzed on 2011-02-20
He's probably just repeating something he heard someone else say.  Really I just wanted to see if there could possibly be anything behind a statement like that.  Thanks for clearing things up ;)

---

### Post by SeijiSensei on 2011-02-20
I will say that, if you have the money, a hardware RAID card and an array of hot-swap drives is a superior solution to software RAID and internal drives.  With software RAID, I've had to use mdadm to replace a failed device manually.  Most hardware RAID cards will rebuild onto a new disk automatically.  With hot-swap drives you can pull a failed drive out of the array from the front panel and replace it without powering down.

---

### Post by frotzed on 2011-02-20
Ah, well, that makes sense.  But when he said that, he wasn't referring to a RAID card and hot swapping.  He was referring to fake RAID versus soft RAID.

But your explanation does make sense.

---

### Post by Stephann on 2011-02-21
For a home or small/medium office, a properly monitored and administered software raid is perfectly safe.  In fact, the only real value for a 'fake' raid is to permit a RAID to exist under a system that wouldn't otherwise support it (Windoze, for example.)  Fake raids are little more than software raids held together at the bios level, and I wouldn't trust them as far as I could throw them.  Just my two cents.

---

### Post by frotzed on 2011-02-21
> **Stephann said:**
> Fake raids are little more than software raids held together at the bios level.

This basically sums up everything I've read on the subject since I started researching a few weeks ago.

---

