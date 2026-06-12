---
title: "Can't create new Steam Library folder"
date: 2020-12-17
forum: Ubuntu/Debian BASED
---

### Post by Hasimir on 2020-12-17
Hi there, I have a problem :)
(what a surprise!)

Steam runs properly but when I go to Settings > Downloads > Steam Library Folders > Add Library Folder > select the desired folder ... I get an error:
```
New Steam library folder must be on a filesystem mounted with execute permissions
```

I run a laptop with 2 drives.
One is the main drive where the system is installed.
The other is a secondary drive I use to store files and big installations (like the games in the Steam library).
It used to work fine (Ubuntu 19.04) but after updating (PopOS 20.10) I now have the aforementioned problem.

Any idea how I could solve it?
Thanks :)

---

### Post by TheFu on 2020-12-19
I don't know anything about Steam, but what file system does this "data disk" have?  Appears that Steam wants to put programs there, not just data.  For native Linux file systems, you can use chmod, if your userid is the owner of the mounted storage.  For non-native file systems, it is harder.

---

### Post by Hasimir on 2020-12-20
It's an NTFS partition.
But it was the same also under Ubuntu 18 and 19.
The problem only presented itself when I switched to PopOs 20.04 and persisted in PopOs 20.10.

Is there a setting file or something I can fix to solve this?

---

### Post by TheFu on 2020-12-20
With NTFS, the only way is to change the options used to mount the storage. That is normally handled in the /etc/fstab file. There may be a GUI way - I don't know it.  You'll need to figure out how to do that.  

There are lots of mount options. For NTFS,  use these:
```
nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002
```

Hope those are useful. **big_writes** helps performance. The **fmask** is what sets all fle permssions in the way steam wants, I suppose. The **dmask** is needed as well.

---

### Post by Frogs Hair on 2020-12-20
Moved to ***Ubuntu/Debian Based***.

---

### Post by Hasimir on 2020-12-20
> **TheFu said:**
> With NTFS, the only way is to change the options used to mount the storage. That is normally handled in the /etc/fstab file. There may be a GUI way - I don't know it.  You'll need to figure out how to do that.  

There are lots of mount options. For NTFS,  use these:
```
nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002
```

Hope those are useful. **big_writes** helps performance. The **fmask** is what sets all fle permssions in the way steam wants, I suppose. The **dmask** is needed as well.

Searching the interwebs on my own I found a bunch of pretty unclear fixes with similar answers.
This is what my options looked like after the "fix" I was able to find:
```
defaults,noatime,utf8,umask=000,dmask=002,fmask=112,uid=1000,gid=1000,x-gvfs-show 0 2
```

Let"s hope it works :)
I'll write back after a quick reboot.

---

### Post by Hasimir on 2020-12-20
It works!
Thank you SO much :D

---

### Post by TheFu on 2020-12-20
> **Hasimir said:**
> Searching the interwebs on my own I found a bunch of pretty unclear fixes with similar answers.
This is what my options looked like after the "fix" I was able to find:
```
defaults,noatime,utf8,umask=000,dmask=002,fmask=112,uid=1000,gid=1000,x-gvfs-show 0 2
```

Let"s hope it works :)
I'll write back after a quick reboot.

Reboot?  Why?  Just **umount** it then **mount -a**

---

