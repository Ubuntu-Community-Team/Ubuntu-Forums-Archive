---
title: "RAID10 - replace disk, arrays will not assemble"
date: 2015-12-03
forum: Server Platforms
---

### Post by ray.s on 2015-12-03
[FONT=Arial]Update 2 at bottom of post

Here's a brief history of how I got here:[/FONT]

[LIST=1]
[*]4x disk Ubuntu 12.04 software RAID10 with 5x partitions (md0 - md4)
[*]1x disk died
[*]mdadm --fail > mdadm --remove > physically removed drive and replace
[*]mdadm --add > disk resync'd perfectly for all partitions
[*]decided to replace all the disks so they were identical
[*]repeat steps 3-4 for remaining 3 disks. 2nd and 3rd disk went perfectly.
[*]after final disk was replaced I added it back to the array but was notified that the file system was in read-only mode.
[*]cat /proc/mdstat revealed that some partitions had dropped out but it was very inconsistent.
[*]I rebooted the machine (probably not the smartest idea)
[*]Machine wouldn't boot (no MBR on the new disk I assume).
[*]Replaced last drive I had taken out. Machine boots to intitramfs prompt but keyboard unresponsive.
[*]Remove last drive so now only the 3x good disks remain.
[*]Boot from Ubuntu Live USB.
[*]Ubuntu disk utility lists the 4x RAID devices says they are inactive and partially assembled.
[*]```
ubuntu@ubuntu:~$ cat /proc/mdstat[INDENT]Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md3 : inactive sdd8[6](S) sdc8[5](S) sdb8[4](S)
      1464837120 blocks super 1.2

md4 : inactive sdd9[6](S) sdc9[5](S) sdb9[4](S)
      718365696 blocks super 1.2

md1 : inactive sdd6[6](S) sdc6[5](S) sdb6[4](S)
      146479104 blocks super 1.2

md2 : inactive sdd7[6](S) sdc7[5](S) sdb7[4](S)
      585931776 blocks super 1.2

md0 : inactive sdd5[6](S) sdc5[5](S) sdb5[4](S)
      14641152 blocks super 1.2

unused devices: <none>[/INDENT]

```
[*]```
ubuntu@ubuntu:~$ sudo mdadm --assemble --verbose /dev/md0 -f /dev/sdb5 /dev/sdc5 /dev/sdd5
```
[/LIST]
```
[INDENT]mdadm: looking for devices for /dev/md0 mdadm: cannot open device /dev/sdb5: Device or resource busy mdadm: /dev/sdb5 has no superblock - assembly aborted[/INDENT]

```[INDENT]
[FONT=Arial]So now I'm a bit stuck! The 3x disks in there were all consistent at the moment that the 4th disk was replaced. SMART checks come out ok (no bad sectors, etc.).[/FONT][/INDENT]
[FONT=Arial]I just need a way to restore the array with 3x disks so I can re-add the 4th. Any thoughts?[/FONT]
[FONT=Arial]Many thanks!


Also, here's the mdadm -E output for /dev/md0's partitions:

[/FONT]```
&#8203;[FONT=arial]ubuntu@ubuntu:~$ sudo mdadm -E /dev/sd[bcd]5[/FONT]
[FONT=arial]/dev/sdb5:[/FONT]
[FONT=arial]          Magic : a92b4efc[/FONT]
[FONT=arial]        Version : 1.2[/FONT]
[FONT=arial]    Feature Map : 0x0[/FONT]
[FONT=arial]     Array UUID : e7f4170b:545b3395:01a8675d:[/FONT][FONT=arial]afa93e43[/FONT]
[FONT=arial]           Name : tardis:0[/FONT]
[FONT=arial]  Creation Time : Tue Aug 20 10:13:48 2013[/FONT]
[FONT=arial]     Raid Level : raid10[/FONT]
[FONT=arial]   Raid Devices : 4[/FONT]

[FONT=arial] Avail Dev Size : 9760768 (4.65 GiB 5.00 GB)[/FONT]
[FONT=arial]     Array Size : 19519488 (9.31 GiB 9.99 GB)[/FONT]
[FONT=arial]  Used Dev Size : 9759744 (4.65 GiB 5.00 GB)[/FONT]
[FONT=arial]    Data Offset : 2048 sectors[/FONT]
[FONT=arial]   Super Offset : 8 sectors[/FONT]
[FONT=arial]          State : clean[/FONT]
[FONT=arial]    Device UUID : 101168e1:b76709af:006e3c80:[/FONT][FONT=arial]308f834b[/FONT]

[FONT=arial]    Update Time : Thu Dec  3 17:41:58 2015[/FONT]
[FONT=arial]       Checksum : 83dae694 - correct[/FONT]
[FONT=arial]         Events : 174[/FONT]

[FONT=arial]         Layout : near=2[/FONT]
[FONT=arial]     Chunk Size : 512K[/FONT]

[FONT=arial]   Device Role : Active device 3[/FONT]
[FONT=arial]   Array State : .AAA ('A' == active, '.' == missing)[/FONT]
[FONT=arial]/dev/sdc5:[/FONT]
[FONT=arial]          Magic : a92b4efc[/FONT]
[FONT=arial]        Version : 1.2[/FONT]
[FONT=arial]    Feature Map : 0x0[/FONT]
[FONT=arial]     Array UUID : e7f4170b:545b3395:01a8675d:[/FONT][FONT=arial]afa93e43[/FONT]
[FONT=arial]           Name : tardis:0[/FONT]
[FONT=arial]  Creation Time : Tue Aug 20 10:13:48 2013[/FONT]
[FONT=arial]     Raid Level : raid10[/FONT]
[FONT=arial]   Raid Devices : 4[/FONT]

[FONT=arial] Avail Dev Size : 9760768 (4.65 GiB 5.00 GB)[/FONT]
[FONT=arial]     Array Size : 19519488 (9.31 GiB 9.99 GB)[/FONT]
[FONT=arial]  Used Dev Size : 9759744 (4.65 GiB 5.00 GB)[/FONT]
[FONT=arial]    Data Offset : 2048 sectors[/FONT]
[FONT=arial]   Super Offset : 8 sectors[/FONT]
[FONT=arial]          State : clean[/FONT]
[FONT=arial]    Device UUID : 15d54fa9:76363f55:140c208f:[/FONT][FONT=arial]8a85eb56[/FONT]

[FONT=arial]    Update Time : Thu Dec  3 17:41:58 2015[/FONT]
[FONT=arial]       Checksum : c440dc7 - correct[/FONT]
[FONT=arial]         Events : 174[/FONT]

[FONT=arial]         Layout : near=2[/FONT]
[FONT=arial]     Chunk Size : 512K[/FONT]

[FONT=arial]   Device Role : Active device 2[/FONT]
[FONT=arial]   Array State : .AAA ('A' == active, '.' == missing)[/FONT]
[FONT=arial]/dev/sdd5:[/FONT]
[FONT=arial]          Magic : a92b4efc[/FONT]
[FONT=arial]        Version : 1.2[/FONT]
[FONT=arial]    Feature Map : 0x0[/FONT]
[FONT=arial]     Array UUID : e7f4170b:545b3395:01a8675d:[/FONT][FONT=arial]afa93e43[/FONT]
[FONT=arial]           Name : tardis:0[/FONT]
[FONT=arial]  Creation Time : Tue Aug 20 10:13:48 2013[/FONT]
[FONT=arial]     Raid Level : raid10[/FONT]
[FONT=arial]   Raid Devices : 4[/FONT]

[FONT=arial] Avail Dev Size : 9760768 (4.65 GiB 5.00 GB)[/FONT]
[FONT=arial]     Array Size : 19519488 (9.31 GiB 9.99 GB)[/FONT]
[FONT=arial]  Used Dev Size : 9759744 (4.65 GiB 5.00 GB)[/FONT]
[FONT=arial]    Data Offset : 2048 sectors[/FONT]
[FONT=arial]   Super Offset : 8 sectors[/FONT]
[FONT=arial]          State : clean[/FONT]
[FONT=arial]    Device UUID : b4693d31:b032c600:0fa3dd6e:[/FONT][FONT=arial]85582983[/FONT]

[FONT=arial]    Update Time : Thu Dec  3 10:09:52 2015[/FONT]
[FONT=arial]       Checksum : 4bb29e9a - correct[/FONT]
[FONT=arial]         Events : 166[/FONT]

[FONT=arial]         Layout : near=2[/FONT]
[FONT=arial]     Chunk Size : 512K[/FONT]

[FONT=arial]   Device Role : Active device 1[/FONT]
[FONT=arial]   Array State : AAAA ('A' == active, '.' == missing)[/FONT]
```[FONT=Arial]


Update 1:

1. Realised the device busy probably meant I had the mdx up and running.
2. Stopped /dev/md0
3. Re-assembled /dev/md0 with the 3 good disks
4. Plugged in the 4th disk
5. Added the 4th disk to the array (had to zero the superblocks)
6. resync'd - hooray!

Now I tried repeating this on /dev/md1 but no luck, instead I get this error:

[/FONT]```
[FONT=arial]ubuntu@ubuntu:~$ sudo mdadm --assemble --verbose /dev/md1 -f /dev/sdb6 /dev/sdc6 /dev/sdd6[/FONT]
[FONT=arial]mdadm: looking for devices for /dev/md1[/FONT]
[FONT=arial]mdadm: /dev/sdb6 is identified as a member of /dev/md1, slot 3.[/FONT]
[FONT=arial]mdadm: /dev/sdc6 is identified as a member of /dev/md1, slot 2.[/FONT]
[FONT=arial]mdadm: /dev/sdd6 is identified as a member of /dev/md1, slot -1.[/FONT]
[FONT=arial]mdadm: no uptodate device for slot 0 of /dev/md1[/FONT]
[FONT=arial]mdadm: no uptodate device for slot 1 of /dev/md1[/FONT]
[FONT=arial]mdadm: added /dev/sdb6 to /dev/md1 as 3[/FONT]
[FONT=arial]mdadm: added /dev/sdd6 to /dev/md1 as -1[/FONT]
[FONT=arial]mdadm: added /dev/sdc6 to /dev/md1 as 2[/FONT]
[FONT=arial]mdadm: /dev/md1 assembled from 2 drives and 1 spare - not enough to start the array.[/FONT]
[FONT=arial]ubuntu@ubuntu:~$ sudo mdadm --detail /dev/md1[/FONT]
[FONT=arial]mdadm: md device /dev/md1 does not appear to be active.[/FONT]
[FONT=arial]ubuntu@ubuntu:~$ cat /proc/mdstat [/FONT]
[FONT=arial]Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] [/FONT]
[FONT=arial]md1 : inactive sdc6[5](S) sdd6[6](S) sdb6[4](S)[/FONT]
[FONT=arial]      146479104 blocks super 1.2[/FONT]

[FONT=arial]md0 : active raid10 sde5[7] sdd5[6] sdb5[4] sdc5[5][/FONT]
[FONT=arial]      9759744 blocks super 1.2 512K chunks 2 near-copies [4/4] [UUUU][/FONT]

[FONT=arial]md3 : inactive sde8[6] sdc8[5] sdb8[4][/FONT]
[FONT=arial]      1464837120 blocks super 1.2[/FONT]

[FONT=arial]md4 : inactive sde9[6] sdc9[5] sdb9[4][/FONT]
[FONT=arial]      718365696 blocks super 1.2[/FONT]

[FONT=arial]md2 : inactive sde7[6](S) sdc7[5](S) sdb7[4](S)[/FONT]
[FONT=arial]      585931776 blocks super 1.2[/FONT]

[FONT=arial]unused devices: <none>[/FONT]
[FONT=arial]ubuntu@ubuntu:~$ sudo mdadm --manage /dev/md1 --add /dev/sde6[/FONT]
[FONT=arial]mdadm: cannot get array info for /dev/md1[/FONT]

```[FONT=Arial]


Update 2:

I created /dev/md1 again and it detected the old array on the disks. I just hit (y) to continue - unsure if that was a good idea or not. The array re-sync'd but now will not mount. It complains that I need to specify a valid filesystem. Using fsck it says that the superblock is invalid. Thoughts?

[/FONT]

---

### Post by darkod on 2015-12-04
You used --create or --assemble? If you used --create without the --assume-clean option then probably you created new array over the old one...

---

