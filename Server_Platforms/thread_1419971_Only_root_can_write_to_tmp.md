---
title: "Only root can write to /tmp"
date: 2010-03-02
forum: Server Platforms
---

### Post by edpatterson on 2010-03-02
8.04 64bit LTS no gui loaded
Very strange. Only the root user can write to /tmp.
I tried to create a cron job for a user and received an error
```

crontab -e
no crontab file for ed - using an empty one
/tmp/crontab.SCQ30O: Permission denied
Creation of temporary crontab file failed - aborting

```
Then I tried a simple touch /tmp/test1 and it failed with a 'touch: cannot touch `/tmp/test1': Permission denied

I tried the Windows fix and rebooted, no change. Only root can write to tmp.

This may sound lame but... using ls /tmp show reversed video (highlighted blue on green) on the servers the the users have access to, just plain blue on the 'broke' one. 

I did a sudo chmod a+w /tmp but do not know if that was a smart thing to do or not...

Ideas on how to fix it or is the chmod fix correct?

Thanks,
Ed

---

### Post by Bachstelze on 2010-03-02
[font=monospace]/tmp[/font] should be chmodded 1777.

```
sudo chmod 1777 /tmp
```

The "reverse" colouring is probably because of the sticky bit.

---

### Post by edpatterson on 2010-03-02
> **Bachstelze said:**
> [font=monospace]/tmp[/font] should be chmodded 1777.

```
sudo chmod 1777 /tmp
```

The "reverse" colouring is probably because of the sticky bit.

Thanks, I have no idea how it got changed in the first place, but that fixed it!

Ed

---

