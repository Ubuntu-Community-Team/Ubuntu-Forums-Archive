---
title: "Hard drive fills up over night"
date: 2009-05-14
forum: Server Platforms
---

### Post by tazizhere on 2009-05-14
Issue fixed - found an old backup on the drive.  Not sure how that happened.  30GB worth of stuff.

Thanks.

---

### Post by cariboo on 2009-05-14
The first thing I would, is make sure that the backups is going to the correct drive. Could open an Applications-->Accessories-->Terminal and type:

```
sudo fdisk -l
```

and also

```
df -h
```

and paste the outputs in your next post.

Good to see you got the problem solved.

---

### Post by windependence on 2009-05-14
This is one reason why you should always try to partition your drive, even for a home desktop machine. That way, if one partition fills up, your whole machine doesn't fail.

Have you checked /var/log to see if it's log files?

-Tim

---

