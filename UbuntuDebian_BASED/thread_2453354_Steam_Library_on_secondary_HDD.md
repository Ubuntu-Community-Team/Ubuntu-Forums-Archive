---
title: "Steam Library on secondary HDD"
date: 2020-11-08
forum: Ubuntu/Debian BASED
---

### Post by Hasimir on 2020-11-08
I can install Steam no problem. But when I try to add a new location for the library, it fails with the error
```
New Steam library folder must be on a filesystem mounted with execute permissions
```

My system runs a Ubuntu distro on it's primary HDD. Then a secondary boot to Win10.
Then on a secondary HDD I have a big NTFS partition where I park most of my data.
That partition is accessible, writable, and no other application gives me the problems Steam is giving me.
Running steam from Win10 I also have no problem setting the library on that drive.

I checked that Win10 Fast Boot option is off.
I tried messing around with mount settings.
I have no idea what else to do.

Previously, with Ubuntu 19.04, I had no problems with Steam, right out of the box.
Now I upgraded to 20.04 (using Pop_OS instead of vanilla Ubuntu) and this happens out of the blue.

Can anyone help me? :oops:

---

### Post by howefield on 2020-11-08
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by ajgreeny on 2020-11-10
I don't use steam and am not a gamer but the error message you showed us suggests that the partition where the data sits must be a Linux filesystem, probably like ext4, not NTFS which does not understand Linux execute (or any other) file permissions.

---

