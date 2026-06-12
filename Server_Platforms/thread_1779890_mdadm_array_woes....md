---
title: "mdadm array woes..."
date: 2011-06-11
forum: Server Platforms
---

### Post by saibaggins on 2011-06-11
I'm currently experiencing a nightmare scenario, and hoping someone
here might be able to help me.

I had an unexpected power failure, restarting and fsck tried to run but failed. rebooting again the
system drive starts but is unable to mount my /home which on a
separate /md1 raid5.

I am able to get to a console where i'm trying to fix the problem.

my devices are
md0 level=10 devices /dev/sda1,/dev/sdb1,/dev/sdc1,/dev/sdd1
md1 level=5 devices /dev/sda5,/dev/sdb3, /dev/sdc3,/dev/sdd3

doing cat /proc/mdstat
shows md1: inactive sdc3[2] sdb3[1] sdd3[3]

and md0: active raid10 sdd1[3] sdc1[2] sdb3[1]`

this makes me wonder if there was a temporary problem with sda after
the powercut (it appears to be fine now)

examining sda1 it appears to be fine (similar to sdb1 etc)
Array state is AAAA
yet md0 appear to be active without sda1 according to /proc/mdstat.

examining sda5 there where it lists the other drives in the array
there is an anomaly

the right hand to columns read:

active sync  /dev/sda5
active sync  /dev/sdc3
active sync  /dev/sdd3
active sync

so there is no mention of sdb3 and the bottom device has no name...

examining the other partitions b3,c3,d3 the RHS of the bottom 4 lines
are identically

removed
active sync  /dev/sdb3
active sync  /dev/sdc3
active sync  /dev/sdd3

so those partitions suggest it is a which is removed.

I would be tempted to try re-adding sda5 to md1, and sda1 to md0.
but the anomaly above makes me concerned this could make things worse
as I really cant afford to loose data on md1 now. I would have thought
the raid5 would still be able to run with 1 drive removed, as the
raid10 appears to be...

finally i should mention attempting to run /dev/md1 i  get errors

cannot start dirty degraded array
failed to run raid set
md: pers->run() failed...

can anyone suggest how i should proceed?

re-add devices to arrays?

---

### Post by rubylaser on 2011-06-11
If you haven't done any writing on the arrays, you don't want to re-add a drive, you'll want to force assemble the array.  Stop md0 if it's running, and then assuming all of your drives pass a SMART test, try to reassemble the array like this.
```
mdadm --assemble --force /dev/md1 /dev/sda5 /dev/sdb3 /dev/sdc3 /dev/sdd3
```

---

### Post by saibaggins on 2011-06-11
Thanks. That has successfully activated the array

sda5, however did make it into the array and it's running degraded with 3/4 devices (as is md0) 

is this the time to re-add the devices to the array? 

for now i can access my data so first thing is to grab some essential back up. thanks for your help. 

mdadm --detail /dev/md1 

shows 'removed' where sda5 should be. Re add?

---

### Post by saibaggins on 2011-06-11
ok, once i'd grabbed my most essential files i decided i might as well go for the re-add. 

i re-added devices successfully to both array. 

however, of concern is how long the recovery is going to take. According to /proc/mdstat, i have over 1000min to wait to resync md1 (with md0 delayed)... I was thinking that since i am re-adding things should be much faster. At that speed the albeit small odd of a second drive failure are disturbing....

---

### Post by YesWeCan on 2011-06-11
> **saibaggins said:**
> ok, once i'd grabbed my most essential files i decided i might as well go for the re-add. 

i re-added devices successfully to both array. 

however, of concern is how long the recovery is going to take. According to /proc/mdstat, i have over 1000min to wait to resync md1 (with md0 delayed)... I was thinking that since i am re-adding things should be much faster. At that speed the albeit small odd of a second drive failure are disturbing....
With RAID5 these are the risks you take. I personally think RAID5 is dangerous. If data safety is important then backup regularly or go for RAID6.

---

### Post by saibaggins on 2011-06-12
hadn't looked at raid6 before, but it does look like a good idea. In practice the resync only took about 90mins as the rate suddenly shot up to 90MB/s after about 1%. 

switching to raid6 would be an arduous process, which would probably also add risk and in any case you can't do away with backups.

---

