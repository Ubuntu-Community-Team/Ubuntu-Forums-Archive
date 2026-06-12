---
title: "mdadm reshape interrupted"
date: 2012-12-29
forum: Server Platforms
---

### Post by zeuborama on 2012-12-29
Hello all and thanks for reading.

up until yesterday I had a RAID5 array with 5 devices.
Today I added another 2TB devices (dame size as the others), first i formattted it right then added it to the raid (it showed up as a spare) then I grew the array. Whilst the reshaping was taking place I had to reboot the pc and then it wouldn't assemble again.
(complained the superblock weren't the same as ,first drive.)

The array wouldn't assemble (I hadn't had time to update mdadm.conf so I examined each drive and the only difference i was finding was that even though they all believed they were part of a 6 drive raid one drive thought that there were only 5 disks in it.
at that stage (i messed it up since). the detail would show that it was growing from 5 to 6 drive and where it was at.

Foolishly I tried to 'fix' it.
Reading the mdadm manual I was told that mdadm --create would not overwrite data, just metadata. so that's what I did, the array was done with all 6 drives. I try to fsck to check how it's doing but i'm told the resource is busy.

Did I lose my data? what can I do now?

let me know what output is needed and I will try to supply it.

---

### Post by Cheesemill on 2012-12-30
You've really messed up your array by running mdadm --create on it.

It *may* be possible to recover it but it would be much quicker to just start again from scratch and restore the data from your backup.

---

