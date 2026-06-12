---
title: "Odd SMART data changes in seagate drive"
date: 2014-12-30
forum: Server Platforms
---

### Post by MakOwner on 2014-12-30
I have a now out of warranty Seagate 1.5TB SATA drive that is exhibiting some behavior I have never seen before.

I typically monitor and track the 5 big failure indicators plus temperature:
```

SMART 5 - Reallocated_Sector_Count
SMART 187 - Reported_Uncorrectable_Errors
SMART 188 - Command_Timeout
SMART 197 - Current_Pending_Sector_Count
SMART 198 - Offline_Uncorrectable

```

It's been my expereince that in general, #5, Reallocated Sector count will increment but never decrement.
Typically I see 187 count go up until the sector is either read or written again and the drives firmware will realocate the sector if needed, and then #5 increments.
187 would go back to zero, but 5 would not.

I have a drive here that will follow that behavior, but I can run a destructive badblocks pass across the device, and the values in both #5 and #187 will drop to zero.
It will stay that way until the next read or write to the (presumably) same sectors.
While the disk has greater than zero #5, it will fail a smartmontools long test, but so long as the values are zero it passes.


I have the drive out of service, but it's just an odd behavior I have not seen before - anyone else seen anything like this?

---

### Post by tgalati4 on 2014-12-30
I don't know what would cause that behavior, but you could try partitioning the drive.  If the badblocks are in a small group, then you can make a partition with some margin on either side and label it "BAD".  Then try making data partitions before and after the "BAD" partition.  I wouldn't use it for an operating system, but for data, static storage, it might be OK.  It won't pass the smartctl -t long test (since that scans the entire drive), but it should pass the *badblocks* test on each good partition.  Of course, this only works if the drive mechanics are working OK otherwise.

You should continue to monitor the 5 parameters and they should remain stable since the "BAD" partition is not being mounted or read at all.  If the drive does have a mechanical issue, you will know soon enough.  If the badblocks are scattered throughout the drive, then it could be motor control, drive control, or a failing head causing the sectors to fail around the disk.

Drives are cheap enough that you just may want to toss it.

---

### Post by kpatz on 2014-12-30
Normally a drive will reallocate spare sectors to replace bad ones, so once that happens, it should function as a "good" drive once again, as this happens transparently.  But if the drive is dying, it could be getting "bad" sectors everywhere.

What utility are you using to do the "destructive bad block pass?"  Once sectors are reallocated they should stay that way, unless it's some sort of Seagate diagnostic tool that resets the reallocation table and makes the bad sectors accessible again.

You might try running the "destructive bad block pass" again, then run a full scan using another utility (such as dd).  See if the reallocated count goes up.  Then scan the drive again with dd.  The reallocated and uncorrectable count should stay the same on the 2nd scan since it'll skip over the bad sectors.  If they keep on going up after multiple scans, the drive is ready for the trash bin.

---

### Post by MakOwner on 2014-12-30
> **kpatz said:**
> Normally a drive will reallocate spare sectors to replace bad ones, so once that happens, it should function as a "good" drive once again, as this happens transparently.  But if the drive is dying, it could be getting "bad" sectors everywhere.

What utility are you using to do the "destructive bad block pass?"  Once sectors are reallocated they should stay that way, unless it's some sort of Seagate diagnostic tool that resets the reallocation table and makes the bad sectors accessible again.

You might try running the "destructive bad block pass" again, then run a full scan using another utility (such as dd).  See if the reallocated count goes up.  Then scan the drive again with dd.  The reallocated and uncorrectable count should stay the same on the 2nd scan since it'll skip over the bad sectors.  If they keep on going up after multiple scans, the drive is ready for the trash bin.


That's been my experience too -- reallocated sector count goes up, never down.

I'm using badblocks -svw for the destructive testing, no seagate utility.


```

Usage: badblocks [-b block_size] [-i input_file] [-o output_file] [-svwnf]
       [-c blocks_at_once] [-d delay_factor_between_reads] [-e max_bad_blocks]
       [-p num_passes] [-t test_pattern [-t test_pattern [...]]]
       device [last_block [first_block]]

```

---

### Post by tgalati4 on 2014-12-31
You need to use *fsck -cc* to mark the bad blocks so that the operating system does not use them.  Otherwise *badblocks* simply reports the bad blocks.  If the drive mechanics are stable, you should get the same list of bad blocks each time it is run.  How the disk drive handles bad sectors (which are different from bad blocks) is proprietary and hidden from the user.  Perhaps a low-level format using a factory program will reset the bad sector table--I don't know.

It's possible that by accessing the bad sectors is causing the disk drive firmware to permanently pull them out of the "good" sector pool.  *Badblocks* is a good way to exercise a new drive and then examine the pending and relocation numbers as a way to validate the disk before using in a critical operation.  I would return a new disk that didn't have a clean record after running *badblocks*.  I would use* fsck -cc* on a drive that has a wonky disk that I need to keep running as a spare or educational machine, but not a critical or production machine.  Linux expects perfect hardware.

---

