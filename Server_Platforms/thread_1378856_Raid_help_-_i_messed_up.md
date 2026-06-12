---
title: "Raid help - i messed up"
date: 2010-01-11
forum: Server Platforms
---

### Post by buck2825 on 2010-01-11
Went to back up my raid.  Before backing up my data I started to format my external HD.  Opened GParted selected HD and deleted the partition and applied the changes.  Here is the mistake, selected the wrong HD I selected my RAID. After I applied the changes I could still access my data, up until I rebooted my server.  

I'm using mdadm for the RAID.    

Help, Please.

---

### Post by buck2825 on 2010-01-12
bump

---

### Post by fjgaude on 2010-01-13
I assume you have three or more drives in the array. Likely the **md** within the kernel doesn't like what it sees. Try this:

```
sudo mdadm --assemble --scan
```

That should bring the array up in a degraded condition with it automatically bringing the re-formatted drive back in.

If that doesn't work, make sure that drive can be added back into the array:

```
sudo mdadm /dev/md[nn] --add /dev/sd[nn]
```

Let us know how you are doing.

---

### Post by buck2825 on 2010-01-13
no this is a raid 1 with two 1.5 TB drives.  i will try your suggestions tonight. 

Thanks.

---

### Post by fjgaude on 2010-01-13
Okay, you should be able to get it working again without data loss.

---

### Post by soltanis on 2010-01-13
I had mdadm running on two disks in RAID 1 as well. The problem was, their filenodes kept changing and so that messed up the array configuration (it ended up splitting into two degraded arrays or sometimes just not working at all). I had to force stop both arrays, then create a new one. That seemed to solve it, though.

---

### Post by buck2825 on 2010-04-17
I rolled back to an off site back up I had it was a couple of months old but I rolled back to this and moved on with my life

thanks for all the help!!!

---

