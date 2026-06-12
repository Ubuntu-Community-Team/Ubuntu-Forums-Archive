---
title: "Can't connect/start up my server"
date: 2008-07-06
forum: Server Platforms
---

### Post by magicplayr2000 on 2008-07-06
My server was working fine a few minutes ago, then I restarted it.  Now it's not starting up properly.  It says Warning: Not loading blacklisted module vesafb.  Once it gets past that, it says that it cannot find /dev/disk-by-uuid/<uuid number>, and that I need to check my /dev/ and /proc/modules.  I'm not sure what caused this/what I can do to fix it.

EDIT: OK, so I get this error starting the newest kernel.  The older kernel works fine, however.  Should I be concerned?

---

### Post by Panos on 2008-07-06
Hello,

I had a similar problem after I upgraded my headless server from 7.10 to 8.04, a couple of days ago. It seems that indeed a new kernel messed up my disk arrangement. For example, one change I discovered was that the (IDE disk) hda designation was no longer valid and it was renamed to sdd (yes, the IDE disk :confused:). 

Anyway, I think your problem may be similar to mine, so you have to find the correct disk arrangement and the new assignments.

So try 
```
sudo mount
```

and then
```
sudo blkid
```

Now you should note down the UUIDs for the devices found in /dev.

Then edit your fstab and correct the UUIDs or, even better, replace all device designations (for example, /dev/sda1) with the corresponding UUIDs.

---

