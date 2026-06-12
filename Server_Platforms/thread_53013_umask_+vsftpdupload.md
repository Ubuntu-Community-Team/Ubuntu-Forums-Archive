---
title: "umask +vsftpd/upload"
date: 2005-07-29
forum: Server Platforms
---

### Post by [pl]ice on 2005-07-29
hi, i can't get right the umask on vsftpd.
after uploading user gets (standard) eg. drwx--------
what mask should i use to get dr-x----
and dr-xr-x-r-x

i thought mask was simply subctracting the values from original ones, eg:
drwx 700
mask 200
dr-x 500

i don't think it's correct.
can someone help me out?thanks!

what i'm trying to do is to allow a user to upload into a dir. but he cannot delete that. any ideas?

---

### Post by heimo on 2005-07-29
This is how I get it:

```

rwxrwxrwx = 777 (full rights)
r-x------ = 500 (what you want)
-w-rwxrwx = 277 (what you need as a mask)

```

---

