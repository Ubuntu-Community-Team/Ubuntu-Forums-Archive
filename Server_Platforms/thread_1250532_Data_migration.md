---
title: "Data migration?"
date: 2009-08-26
forum: Server Platforms
---

### Post by m3bik on 2009-08-26
I'm upgrading the hard drive in one of my test servers.

I know how to back up files and what not...

But is there an easy to way to back up an entire hard drive (including files, ubuntu os, settings, etc) and place it on a new hard drive?

---

### Post by jocampo on 2009-08-26
> **m3bik said:**
> I'm upgrading the hard drive in one of my test servers.

I know how to back up files and what not...

But is there an easy to way to back up an entire hard drive (including files, ubuntu os, settings, etc) and place it on a new hard drive?

"dd" command will let you clone a complete disk/partiton. Only drawback is that is an exact replica, so will take same space. If you want to clone sda, this is what you should do

```

sudo dd if=/dev/sda of=/media/disk1/sda-copy.img

```

To restore

```

sudo dd if=/media/disk1/sda-copy.img of=/dev/sda

```

disk1 is your external media, mounted here as a destination. Be sure your source is NOT in use or mounted!

---

