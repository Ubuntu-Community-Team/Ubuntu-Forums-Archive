---
title: "can anyone tell me why these files appear?"
date: 2010-10-27
forum: Server Platforms
---

### Post by gobbledigook on 2010-10-27
hi there! 

i use ubuntu 10.04 and recently i installed an extra 2tb drive, i use mhddfs to stitch it all together, but since the last drive was added i keep getting tmp files turning up in the dir all the drives are mounted in :

```
-rwxrwxrwx  1 user   user          0 2010-10-16 17:15 RWR37.tmp
-rwxrwxrwx  1 user   user          0 2010-10-18 18:59 RWR38.tmp
-rwxrwxrwx  1 user   user          0 2010-10-16 17:45 RWR3A.tmp
-rwxrwxrwx  1 user   user          0 2010-10-16 18:15 RWR3D.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 02:45 RWR3E.tmp
-rwxrwxrwx  1 user   user          0 2010-10-16 18:45 RWR40.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 19:14 RWR41.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 03:15 RWR42.tmp
-rwxrwxrwx  1 user   user          0 2010-10-16 19:15 RWR43.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 19:44 RWR44.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 03:45 RWR45.tmp
-rwxrwxrwx  1 user   user          0 2010-10-16 19:45 RWR46.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 04:15 RWR47.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 20:14 RWR48.tmp
-rwxrwxrwx  1 user   user          0 2010-10-16 20:15 RWR49.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 04:45 RWR4A.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 20:44 RWR4B.tmp
-rwxrwxrwx  1 user   user          0 2010-10-16 20:45 RWR4C.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 05:15 RWR4D.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 21:14 RWR4E.tmp
-rwxrwxrwx  1 user   user          0 2010-10-16 21:15 RWR4F.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 05:45 RWR50.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 21:44 RWR51.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 06:15 RWR52.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 22:14 RWR53.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 06:45 RWR54.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 22:44 RWR55.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 07:15 RWR56.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 23:14 RWR57.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 07:45 RWR58.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 08:15 RWR5A.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 23:44 RWR5B.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 08:45 RWR5C.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 09:15 RWR5E.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 09:45 RWR60.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 10:15 RWR62.tmp
-rwxrwxrwx  1 user   user          0 2010-10-18 00:14 RWR63.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 10:45 RWR64.tmp
-rwxrwxrwx  1 user   user          0 2010-10-18 00:44 RWR65.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 11:15 RWR66.tmp
-rwxrwxrwx  1 user   user          0 2010-10-17 11:45 RWR68.tmp

```

any ideas why? what for? etc...


greatly appreciated :)

---

### Post by gobbledigook on 2010-11-01
*bump*

any ideas? mhddfs uses fuse to join all my drives together into one

---

### Post by dtfinch on 2010-11-01
No idea. You could run "lsof" to see if anything currently has one of those files open. Whatever it is, it's creating them at a half hour interval.

---

### Post by gobbledigook on 2010-12-14
that isn't giving any output related to those files :( it does show samba using some files (obviously someones watching a movie!) but not those...

---

### Post by sanderd17 on 2010-12-14
could you look at your processes? And maybe look at the contents of such a file (if it's readable)

---

