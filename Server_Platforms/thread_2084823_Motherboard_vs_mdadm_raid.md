---
title: "Motherboard vs mdadm raid"
date: 2012-11-16
forum: Server Platforms
---

### Post by smb2004 on 2012-11-16
Hello,

I currently have a server running and want to introduce a RAID 1 to provide a little peace of mind.  I have found some threads discussing using mdadm for this, but my motherboard supports RAID.  Is it possible to set up the RAID from BIOS without reformatting the drives?

Which would be a better setup?

---

### Post by darkod on 2012-11-16
You can't make the fakeraid (bios raid) without formatting the disks (destroying the data).

Software raid (mdadm) would probably be better and will not depend on the board chip. Even if the board dies, you can connect the disk(s) to another linux machine and read the data without any issues.

For fakeraid or hardware raid you would have to find an identical controller, and it's still a question whether you could read the data.

Also, which might help you a lot, you can actually set up the mdadm raid1 without moving the data on a temporary location. If the data is only on one disk right now.

You will create the raid1 with only the second disk and one missing member.
Once the array is running, copy the data from the first disk that now holds it to the array.
Then add the first disk as the missing member and let it sync the array.

If you need more detailed info, just ask. But there are plenty tutorials on google how to convert single disk into raid1 mdadm array. I repeat, only if all the data is on one disk right now.

---

### Post by sandyd on 2012-11-16
> **smb2004 said:**
> Hello,

I currently have a server running and want to introduce a RAID 1 to provide a little peace of mind.  I have found some threads discussing using mdadm for this, but my motherboard supports RAID.  Is it possible to set up the RAID from BIOS without reformatting the drives?

Which would be a better setup?

Does your motherboard have hardware raid or fakeraid (JMB/JMicron).

If it has HW raid, be wary. If your controller fails, you can't replace it because its on the computer directly. You can't move it to another computer with a HW raid array, UNLESS it uses the same chipset type.

There is no much difference between fakeraid and software raid.

BTW, as darkod said above, you _will_ lose your data if you convert to fakeraid or hw raid

---

### Post by CharlesA on 2012-11-16
What both the other said. Also: RAID isn't a substitute for backups - if you don't keep backups and your drive/controller/whatever dies, you just lost your data. If you have a backup and your controller goes out, you can just grab another one and restore the data to the array.

---

