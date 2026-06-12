---
title: "starting degraded raid 5 array"
date: 2010-06-11
forum: Server Platforms
---

### Post by JigglyWiggly_ on 2010-06-11
Ok so my servers 7 hds in raid 5  all was working well until one of them died. The HD that died sort of works it can read like half a file also freezes on the benchmark test in disk utility.  Unfortunate when i take it out on boot it says.  The drive for /media_kbt is not ready or present press s to skip or m for manual recovery. I hit s and then go to disk utility. But i can't start or add disks to the array.

Here is me trying to do random stuff
```
administrator@3dslice-host:~$ sudo mdadm --stop /dev/md0
[sudo] password for administrator: 
mdadm: metadata format 00.90 unknown, ignored.
mdadm: stopped /dev/md0
administrator@3dslice-host:~$ sudo mdadm --add /dev/md0 /dev/sda1
mdadm: metadata format 00.90 unknown, ignored.
mdadm: cannot get array info for /dev/md0
administrator@3dslice-host:~$ sudo mdadm --add /dev/md0 /dev/sda
mdadm: metadata format 00.90 unknown, ignored.
mdadm: error opening /dev/md0: No such file or directory
administrator@3dslice-host:~$ sudo mdadm --assemble --scan
mdadm: metadata format 00.90 unknown, ignored.
mdadm: SET_ARRAY_INFO failed for /dev/md0: Device or resource busy
administrator@3dslice-host:~$ 

```

---

### Post by JigglyWiggly_ on 2010-06-11
Here is how it looks inside Disk-utility
[img]http://img29.imageshack.us/img29/7318/screenshotvh.png[/img]

---

### Post by JigglyWiggly_ on 2010-06-11
Also if I stop and try starting it I get this
```
Error assembling array: mdadm exited with exit code 1: mdadm: metadata format 00.90 unknown, ignored.
mdadm: failed to RUN_ARRAY /dev/md0: Input/output error
mdadm: Not enough devices to start the array while not clean - consider --force.
```

EDIT: I can access my data with that hard drive that is partially broken, what the hell? Why did they ship something that's broken!

I can't recover any dad from that broken hd because in the middle of the trasnfer it will freeze.

EDIT2: Uh it booted with the broken hd, then it was going to resync itself, I cancelled it because it could never actually resync itself. I told it to remove that hd from the array, and it didn't complain, now it just says DEGRADED on it.
Took the HD out, and now it's checking for disc errors, will wait till that's over. Hopefully then I can add my new hd to the array and it will all be good.

But this brings up a dilemma, what if the HD was really dead? It makes you wonder how secure these things really are... even Windows RAID 5 never did this to me. Albeit that is slow as hell.
EDIT3: Ok I think it will work, I told it to add a spare, (not add space) to the array, and it says recovering.
Hopefully all will be well.

---

