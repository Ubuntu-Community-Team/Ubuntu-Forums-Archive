---
title: "Migrating raid6 down to raid5...time to finish=world end!"
date: 2017-08-04
forum: Server Platforms
---

### Post by KillerKelvUK on 2017-08-04
So my 4x 4TB raid6 was running short on space, I've plenty of backup and decided I don't need the 2 disk redundancy of raid6 so I decided to migrate it to a raid5 instead.

```

mdadm --grow /dev/md0 --level=raid5 --raid-devices=3 --backup-file=/home/me/mdadm-backupfile

```

The above triggered the process, only using 3 disks as the posts/guides I've found advise to drop to 3+hotspare and then increase to 4 once at raid5.  I started this process 8 hours ago with full expectation it would take a long long time.

```

Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10]
md0 : active raid6 sdf1[3] sde1[2] sdc1[1] sdb1[0]
      7813771264 blocks super 1.2 level 6, 512k chunk, algorithm 2 [4/4] [UUUU]
      [>....................]  reshape =  0.0% (1/3906885632) finish=120592536461.4min speed=0K/se
c
      bitmap: 0/30 pages [0KB], 65536KB chunk

```

However the above is the progress I'm seeing where only the time to finish increases with nothing else evident other than some dmesg output following the start of the process...

```

[Fri Aug  4 12:05:37 2017] md: reshape of RAID array md0
[Fri Aug  4 12:12:52 2017] SGI XFS with ACLs, security attributes, realtime, no debug enabled
[Fri Aug  4 12:12:52 2017] JFS: nTxBlock = 8192, nTxLock = 65536
[Fri Aug  4 12:12:52 2017] ntfs: driver 2.1.32 [Flags: R/O MODULE].
[Fri Aug  4 12:12:52 2017] QNX4 filesystem 0.2.3 registered.

```


Any advice on whether this is normal behaviour and/or what I should be expecting would be appreciated?

Thanks,

K

---

### Post by darkod on 2017-08-04
I haven't used grow, but did you check the tutorials and man page for the correct syntax? Aren't you supposed to list the devices in the grow command?

---

### Post by KillerKelvUK on 2017-08-04
I believe so, the man page doesn't advise that you have to list the devices specifically from what I've read and the various articles online whilst dated are consistent with one another and with the man page from what I can tell...

[http://www.tjansson.dk/2013/09/migrate-from-raid-6-to-raid-5-with-mdadm/](http://www.tjansson.dk/2013/09/migrate-from-raid-6-to-raid-5-with-mdadm/)
[http://www.linuxquestions.org/questions/linux-general-1/how-to-migrate-from-raid-6-to-raid-5-using-mdadm-and-lvm-939508/](http://www.linuxquestions.org/questions/linux-general-1/how-to-migrate-from-raid-6-to-raid-5-using-mdadm-and-lvm-939508/)

...and the command was accepted without error with a dmesg output of a reshape which is consistent with my expectations, however I've never done this before so other than the command and "a long time" I'm not sure what to expect in truth.

---

### Post by darkod on 2017-08-04
Well, yes, the grow command seems to be correct. Has cat showed it moved from 0%?

---

### Post by KillerKelvUK on 2017-08-04
Nope, still at zero...I have a watch on /proc/mdstat and the only value to change is the finish time, has been running for nearly 11hrs now.

---

### Post by KillerKelvUK on 2017-08-04
Okay so I grep'd my syslog and found the following...

```

Aug  4 12:05:11 blackserver systemd[1]: Created slice system-mdadm\x2dgrow\x2dcontinue.slice.
Aug  4 12:05:11 blackserver systemd[1]: mdadm-grow-continue@md0.service: Main process exited, code=exited, status=2/INVALIDARGUMENT
Aug  4 12:05:11 blackserver systemd[1]: mdadm-grow-continue@md0.service: Unit entered failed state.
Aug  4 12:05:11 blackserver systemd[1]: mdadm-grow-continue@md0.service: Failed with result 'exit-code'.

```

The timestamp correlates with when I started the process/issued the first command.  However /proc/mdstat still shows what I posted in the OP that its working but 0.0%.

Any idea how I delve into what is meant by "2/INVALIDARGUMENT"?

---

### Post by KillerKelvUK on 2017-08-05
Okay so no further error information I can find to elaborate on the systemd service error.

Stopping the array and then restarting it caused me a head ache as mdadm was reporting there was no metadata in the backup file so I ended up with the following command to restart the array...

```

mdadm --assemble --verbose --force --invalid-backup /dev/md0 --backup-file=/home/me/mdadm-backupfile /dev/sd[bcef]1

```

This restored the array but the reshape was still present but again not progressing and systemd was again reporting the 'mdadm-grow-continue@md0.service' as failed but this time "status=1/FAILURE".

Lots of googling and reading but I've now managed to get the reshape progressing by opening a new terminal and issuing the following command...

```

mdadm --grow --continue /dev/md0 --backup-file=/home/me/mdadm-backupfile

```

When I issue the command it seems to hang but by inspecting /proc/mdstat in another terminal I now see progress and the mdadm backup file has increased in size by 100% to @ 33MB.

Hoping this is now working but am obviously still concerned about why it failed in the first instance?

---

