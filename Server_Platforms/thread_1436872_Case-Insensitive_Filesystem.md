---
title: "Case-Insensitive Filesystem"
date: 2010-03-23
forum: Server Platforms
---

### Post by WitchCraft on 2010-03-23
What methods are there to make the Linux filesystem case-INSENSITIVE ?

I have asp.net applications developed on Windows, but there are always issues with capitalization/spelling on mono when putting it on Linux.

One way is to mount a localhost SMB share to /var/www.
Are there any others ?

---

### Post by cdenley on 2010-03-23
```

sudo apt-get install ciopfs
sudo mkdir /media/casei
sudo ciopfs /var/www /media/casei
ls -l /media/casei/index.aspx
ls -l /media/casei/INDEX.ASPX

```

---

### Post by WitchCraft on 2010-03-24
> **cdenley said:**
> ```

sudo apt-get install ciopfs
sudo mkdir /media/casei
sudo ciopfs /var/www /media/casei
ls -l /media/casei/index.aspx
ls -l /media/casei/INDEX.ASPX

```

Excellent. Thanks !

---

### Post by WitchCraft on 2010-05-29
WTF ? This just maps lowercase filenames to lowercase
It doesn't map uppercase filenames, and when you do ls, it's case-sensitive...

Do I need to add any options to ciopfs (no man page, help is not useful...)
ciopfs /mnt/sensitive/ /mnt/insensitive/

This is not case-insensitive, this is bs.

---

