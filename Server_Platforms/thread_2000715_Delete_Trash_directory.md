---
title: "Delete Trash directory"
date: 2012-06-10
forum: Server Platforms
---

### Post by computerfox on 2012-06-10
Hello all,

I was wondering if there is a way to delete the .Trash directory in Ubuntu Server 11 because it's using up a large sum of my hard drive.

-FOX

---

### Post by codemaniac on 2012-06-10
Instead of deleting the directory all together you can try empty the directory by deleting the contents of it .

---

### Post by computerfox on 2012-06-10
thanks maniac for your reply.  yes, that's what i meant (HAHA).  the issue is that for some reason i can't find it at all.  i checked the root and also i tried to find it at the mount path, but i didn't find it at all.

---

### Post by codemaniac on 2012-06-10
> **computerfox said:**
> thanks maniac for your reply.  yes, that's what i meant (HAHA).  the issue is that for some reason i can't find it at all.  i checked the root and also i tried to find it at the mount path, but i didn't find it at all.

Just curious , are you getting overwhelmed by bulky log files ?

If you have removed a file using rm command there is no way it can go to trash , it is gone forever .

---

### Post by computerfox on 2012-06-10
you know, that was actually my first assumption and i just realized that one reason that i can't find the trash folder is because when you use rm, it removes it forever.  so i think i'm going back to my initial thought.  what is the best way to remove those logs?

---

### Post by codemaniac on 2012-06-10
it actually depends on your requirement what you want to keep and what you dont .There are different kind of log files available in a *NIX server for different running services .

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

The best idea may be, trying to write up a bash script that gets fired from cron and does the log cleanup activity at cetain interval of time.

---

### Post by computerfox on 2012-06-10
i'm looking at logrotate, but  i'm guessing it needs some special parameters and it can't be run simply by calling "logrotate"

---

### Post by computerfox on 2012-06-10
i got it cleaned up now..... the log that was killing me was /var/log.  is this normal?

---

### Post by codemaniac on 2012-06-10
Check the disk usage of the /var/log directory , if it is eating away a lot of space .

```
du -sh /var/log
```

---

### Post by Bushflyr on 2012-06-10
/var/log is the directory that all your log files go into. It will simply continue to grow as various programs log their various messages. If you want it to not grow you need to turn off logging in whatever programs are logging there.  If you want to keep logging but have it not grow into a bloated mess you can use:

```
sudo rm /var/log/*.gz
```

to get rid of all the old archived logs but keep the most recent ones.

---

