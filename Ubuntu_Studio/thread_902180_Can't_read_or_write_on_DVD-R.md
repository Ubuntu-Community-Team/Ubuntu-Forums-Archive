---
title: "Can't read or write on DVD-R"
date: 2008-08-27
forum: Ubuntu Studio
---

### Post by PacoCrespo on 2008-08-27
I can't read or write on DVD-R, I have no problems with DVD+R.

I read it was a problem with the  fstab file and I made the following change:

from;
"/dev/scd0  /media/cdrom0 udf,iso9660 user,noauto 0 0"

to:
"/dev/scd0  /media/cdrom0 auto user,noauto,exec,utf8 0 0"

---

### Post by thorgal on 2008-08-27
could simply be your hardware.
Some DVD drives can only handle one of the two formats. It is the case on my old Dell Latitude D800 laptop, can only handle DVD+R and DVD+RW. Read the specs of your DVD drive first.

---

### Post by PacoCrespo on 2008-08-28
Just some weeks ago my laptop works with windows and I was able to write, please, any other idea????

Thanks a lot....

---

