---
title: "Recommendations for a good backup app?"
date: 2010-04-03
forum: Server Platforms
---

### Post by zoomiest on 2010-04-03
I have just set up a simple back-up box in a remote building with a 2TB drive. Its set up for ssh now, but... 

Does the community recommend any good open source back up application that could set up to support small business? 

- automated schedule?
- uses tar format (optional)
- ability to restore a single file at a time.
- encrypted traffic.
- fast.

Thanks in advance.

---

### Post by KB1JWQ on 2010-04-03
I like bacula, others love Amanda.

---

### Post by HermanAB on 2010-04-04
Howdy,

Rsync is your friend.

Also check out rbackup and dervish.  Google will find them.

---

### Post by NightwishFan on 2010-04-04
I second rsync.
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by iissmart on 2010-04-04
Third rsync. Very versatile tool.

---

### Post by Lucky. on 2010-04-04
4th rsync!  For what it's worth.

---

### Post by doogy2004 on 2010-04-04
I use JungleDisk, it meets most of your requirements.

[http://www.jungledisk.com/](http://www.jungledisk.com/)

---

### Post by psusi on 2010-04-04
If you want to backup a server using tar, then just make a cron job to run tar.  Personally I've been trying to migrate to dump lately.  It seems to be faster than tar since it directly accesses the filesystem.

---

