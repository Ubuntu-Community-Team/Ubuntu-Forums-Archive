---
title: "LVM snapshots generating weird syslog messages on a new server"
date: 2009-05-15
forum: Server Platforms
---

### Post by Slasheri on 2009-05-15
Hello!

At first some background:

I have installed Ubuntu Hardy 8.04 on a brand new HP DL380 G5 server, featuring ECC corrected RAM, hardware raid-5 (cciss driver, P400 controller with 256MB BBWC) and enterprise grade SAS drives.

On that server I have several virtual machines, using LVM volumes as drives. I have installed newer KVM packages from Ubuntu Virtualization Team because there were so many issues with the older KVM included in Hardy.

The problem:

When I try to take a snapshot from an LVM volume (the LV that some VM is using), sometimes following weird messages appear in kern.log:

May 15 09:18:24 vmh kernel: [38080.001870] Buffer I/O error on device dm-12, logical block 2621438
May 15 09:18:24 vmh kernel: [38080.001917] attempt to access beyond end of device
May 15 09:18:24 vmh kernel: [38080.001924] dm-12: rw=0, want=20971512, limit=18882560
May 15 09:18:24 vmh kernel: [38080.001928] Buffer I/O error on device dm-12, logical block 2621438

That can happen even if all virtual machines are stopped (so nothing should be accessing either the original LV or the snapshot LV). Those messages just shortly appear after issuing the lvcreate -s command and nothing else. Issuing that same command again, after having removed the snapshot, usually doesn't reproduce the issue.

There is no problem reading the created snapshot, despite those messages. And no file system issues either, doing fsck to all volumes reports clean and overall performance is good. And all system management tools from HP report no issues either, all components inside the server with redundancy are ok.

I just have no idea what could be causing that message, and if it's safe to ignore because no other issues have been found so far.

Thanks for any hints!

---

### Post by Slasheri on 2009-05-15
It seems that the problem was probably caused by a bug that triggered sometimes when the snapshot size was larger than the actual LV the snapshot was taken from. Now when I always specify the snapshot size as less than the LV size, the issue no longer happens.

---

