---
title: "chown on /media/foo not permitted as root!"
date: 2009-08-12
forum: Security
---

### Post by biggerben on 2009-08-12
I have a fstab-mounted /media/backup (ext4) and an automounted /media/external (FAT32)
I recently gave my roommate an account on my box, and don't want him to have access to either one, or my /home (obv).

I changed options in fstab to defaults,utf8,umask=0000,uid=1000,gid=1000, is that correct?

I chmod'ed my /home/me to 700.

I tried to chown /media/external to me:me, but get the error
```
chown: changing ownership of `/media/external': Operation not permitted

```

first: how do i fix that last error (it's auto-mount, so i can't do anything in fstab!)
second: is everything secured like now? will it still be after a restart?

---

### Post by bodhi.zazen on 2009-08-13
Your umask value is wrong and you can not use chown or chmod on FAT or NTFS partitions.

Try umask=077

---

### Post by biggerben on 2009-08-13
> **bodhi.zazen said:**
> Your umask value is wrong and you can not use chown or chmod on FAT or NTFS partitions.

Try umask=700


Uh, you mean 077, right?

---

### Post by Nepherte on 2009-08-13
Yes, he probably does.

---

### Post by bodhi.zazen on 2009-08-13
Ooops ... Fixed my post

---

