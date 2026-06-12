---
title: "Expert help needed: mdadm resync fsck or ???"
date: 2005-11-30
forum: Server Platforms
---

### Post by f1d094 on 2005-11-30
I have a degraded 4 drive RAID5. I have determined that the problem was entirely software related, but I still cannot get my array back to a clean, non-degraded state.

The basics:

/dev/sdd3 - Ok
/dev/sdc3 - Ok
/dev/sdb3 - Original drive marked faulty. Has been attempted to be hotadded back into the array 3 times. Each time, the process fails at 99% and /dev/sda3 spews about 50 data errors (same type different blocks). /dev/sdb3 is then simply re-listed as spare and then /dev/sda3 is also marked faulty.
/dev/sda3 - "mdadm --assemble --force" is able to put this drive back into the array, after which it seems it can be used (read only of course) quite happily.

Analysis so far:

I think I simply have a tiny amount of parity/data corruption that is somehow isolated to /dev/sda3. If I could clean these prior to adding the drive back into the array, the "hot add" of /dev/sdb3 would be successful.

There are several approaches I can think of to approach this problem, but I do not know their safety or sanity. I have scoured the help sites and googled until my eyes are bleeding to no avail. I cannot find any documentation describing any of the following:
[LIST=1]
[*]**fsck the degraded filesystem** - Will this accomplish anything? I am afraid to write any data to the degraded drives and lose any potential work arounds.
[*]**"mdadm --assemble --update=resync" the degraded array** - I am assuming that there isn't enough parity data to rebuild whatever died on /dev/sda3, but since its such a tiny amount of data, is it possible? Once again, I am afraid to write any data to the degraded drives until I know what I am doing.
[*]**Force mdadm to mark /dev/sdb3 "faulty" and then force it back into the array. Once this has been accomplished, do the  "mdadm --assemble --update=resync" on the now "non-degraded" array.** Is this possible? Will it accomplish anything? I am ignorant on how mdadm "hot-adds" a drive into an array. Does it do blatant destructive writing? Or does it actually try and "resynchronize" target data with the other devices...which of course would normally result in blanket writing of data in the case of a new blank drive. If it is the former, then I would expect that my old data is still there and intact, and md is just confused about how to talk to it.
[*]**Move the data off-line and just rebuild the raid** Yes, I've already thought about this...but there are several challenges with this idea as well. First off, I have > 460GB of data on this. Secondly, the only viable way to off-load the data would be via SATA, which are all currently occupied by the aforementioned drives. So even if I cheated, and plugged a backup drive into /dev/sdb3, how do I get the data back onto the device once the raid is restored? I suppose I could buy some heafty 500gb usb drives, and copy these data to them? But jesus...400+ GB of data via USB? I could die of old age....
[/LIST]

If you have any documentation specifically addressing *ANY* or all of the above situations please let me know.

I also have [this post]("http://www.ubuntuforums.org/showthread.php?t=96944") which describes the history of this problem if the background on how I got where I am is of any significance.

**Addendum:** I just tried to set /dev/sdb3 to faulty and then do "mdadm --assemble --force /dev/md0". It seems that since 3 is enough to run on, mdadm decides that the extra drive should just be a spare...how can I force it into the array without using "build" or "create"? Will the build/create options work with assemble mode?

---

