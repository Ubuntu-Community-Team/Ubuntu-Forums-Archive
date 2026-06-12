---
title: "edit files in mounted .image file?"
date: 2010-03-24
forum: Server Platforms
---

### Post by gobbledigook on 2010-03-24
Hi!

a friend of mines laptop died a few weeks ago and i said i would extract data off the drive for her... did this with dd and created a .image file. I have this image mounted so it is browseable, and we can copy files from it however i am unable to delete files from it? 

You'd think it was not a big deal... but i'm running out of space!! and the .image is 90 odd gb. I know i "could" just get the disk and copy the files off she wants... but that would be too easy ;)

any ideas? or should i just go grab my screwdriver ? :)

---

### Post by cdenley on 2010-03-24
You should be able to write to a mounted image. How did you mount it?
```

cat /proc/mounts

```
Are you sure it isn't a permissions issue? How would writing to the image help with your limited disk space? Are you planning on deleting files so you can shrink the image or something? Simply deleting files won't decrease the size of the filesystem image.

---

