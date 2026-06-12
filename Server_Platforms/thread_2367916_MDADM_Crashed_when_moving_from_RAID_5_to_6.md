---
title: "MDADM Crashed when moving from RAID 5 to 6"
date: 2017-08-04
forum: Server Platforms
---

### Post by chrishunter2 on 2017-08-04
Hi, I decided to try and improve the reliability of my RAID array, but adding a spare drive and moving to a 5 disk RAID 6. Power failure stopped this from completing and upon booting got the error:

```

[COLOR=#000000][FONT=&amp]mdadm: Failed to find backup of critical section
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]mdadm: Failed to restore critical section for reshape, sorry. 
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]Possibly you needed to specify the --backup-file
[/FONT][/COLOR]
```

I promptly used my backup file I specified which didn't help. After looking at it, it appears to be a 25M file of nulls, not helpful.

I reviewed other threads, and the most similar appeared to be this one
[https://ubuntuforums.org/showthread.php?t=2133576](https://ubuntuforums.org/showthread.php?t=2133576)

Which initially suggests the backup file (which didn't really help), or by rebuilding the old array manually.

Running

```

[COLOR=#000000][FONT=&amp]mdadm -CR /dev/md0 --metadata=1.2 -n5 -l4 -c512 /dev/sd[abcd] --assume-clean
[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp]

Creates a "RAID" array, but isn't mountable, as I don't think it created it correctly so I just get the bad superblock error. Does anyone have any suggestions on what I could do instead, apart from restoring from backup as that will take days unless I have to.

[EDIT]
If it helps at all, I still have the superblock details from a spare that was on the array during the move to RAID 6 that has all of the correct information (excluding the obvious device role and checksum). Could that be used to recreate the original superblocks?
[/EDIT][/FONT][/COLOR]

---

