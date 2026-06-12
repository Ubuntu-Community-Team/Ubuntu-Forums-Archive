---
title: "ZFS pool not recognized in new install"
date: 2018-07-20
forum: Server Platforms
---

### Post by laceiba2 on 2018-07-20
I have a nicely functioning install of 16.04, but want to give 18.04 a spin. I removed my functioning SSD with 16.04 and plugged in a new one for the new install. 18.04 is up and running and I have installed the necessary zfsutils-linux package. My pool consists for 4 drives (2 mirrored pairs). In 16.04, they show up no problem. When I do a zpool status in 18.04, nothing shows up at all. The drives aren't being mounted, nor can zfs see any inactive pools. If I remember correctly to when I set the pool up, I created the pool and then wound up reinstalling the OS a little while later. The pool immediately showed up without me having to import or recreate it. This does not seem to be the case anymore. Do I need to export the pool first before plugging the new SSD back in? Ultimately, I want to confirm that things are working in 18.04 before I switch and I would like to leave my pool alone in 16.04, if possible. Thanks in advance for any help.

---

### Post by lukeiamyourfather on 2018-07-23
This command will show pools that can be imported.

```
sudo zpool import
```

If the pool you want is listed then it can be imported with this command.

```
sudo zpool import yourpoolname
```

ZFS uses a unique host identifier to determine whether the pool is in the same machine still. In your case it's obviously different so ZFS just left the pool alone. If you didn't explicitly export the pool from the system before then you might have to use "-f" option on the import which forces it to import the pool even if it was never exported properly from another system.

---

