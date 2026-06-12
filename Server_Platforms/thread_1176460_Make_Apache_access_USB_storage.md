---
title: "Make Apache access USB storage"
date: 2009-06-02
forum: Server Platforms
---

### Post by OMA2k on 2009-06-02
I'm running Apache in a tablet with Netbook Remix and I need to access USB thumb drives from a local PHP application running in the same machine. How can I make the /media/disk (or whatever it's the label) directory readable by PHP?

The only method I've found is editing "/etc/apache2/envvars" and change the user and group from "www-data"/"wwwdata" to "myuser"/"root", so it matches the user and group of the /media/disk directory. But I suspect that might be a security risk, right?

---

### Post by cdenley on 2009-06-02
> **OMA2k said:**
> I'm running Apache in a tablet with Netbook Remix and I need to access USB thumb drives from a local PHP application running in the same machine. How can I make the /media/disk (or whatever it's the label) directory readable by PHP?

The only method I've found is editing "/etc/apache2/envvars" and change the user and group from "www-data"/"wwwdata" to "myuser"/"root", so it matches the user and group of the /media/disk directory. But I suspect that might be a security risk, right?

You definitely don't want to run apache as root. You just need to give www-data permission to read your USB drive. Assuming you're using a FAT or FAT32 filesystem, you must do this at mount time.
```

sudo mount -o dmask=022,fmask=133 /dev/sdb1 /media/disk

```

---

