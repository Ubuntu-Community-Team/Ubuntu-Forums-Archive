---
title: "Figuring this out"
date: 2018-09-18
forum: Ubuntu, Linux and OS Chat
---

### Post by jdeiros on 2018-09-18
```
lrwxrwxrwx    1 root     root            73 Sep 15 19:53 ddecomd.log -> /vmfs/volumes/55788775-1acaf4c1-37db-a46c2a38969e/scratch/log/ddecomd.log
```

How can I recreate this for another log? As this is one that already works.

This one was done automatically, but my others weren't.

I have all my logs writing to a SAN at /vmfs/volumes/55788775-1acaf4c1-37db-a46c2a38969e/scratch/log but my server only knows how to read from ~/var/log and I can't change it's defaults

I was thinking to ```
touch syslog.log | ln -s syslog.log /vmfs/volumes/55788775-1acaf4c1-37db-a46c2a38969e/scratch/log/syslog.log 
```

This is the part I am stuck on thought, I don't know the proper terminology to look it up nor how to do it. but I do know I want it to look like this..maybe? Help?

```
lrwxrwxrwx    1 root     root            73 Sep 15 19:53 syslog.log -> /vmfs/volumes/55788775-1acaf4c1-37db-a46c2a38969e/scratch/log/syslog.log
```

---

### Post by cariboo on 2018-09-19
TRy:

```
cat /var/log/syslog.log |less
```

**Note:** there already is a log file called simply syslog in /var/log

---

### Post by jdeiros on 2018-09-19
> **cariboo said:**
> TRy:

```
cat /var/log/syslog.log |less
```

**Note:** there already is a log file called simply syslog in /var/log

The things is I already tried that, and the person who built this told me that he had to move the default locations to the SAN on site because the microSD that the ESXi OS runs off is too small.

That's why I'm asking about the links; the logs would still be stored on the SAN but I'd have a link in /var/log/ called syslog.log

Do I make sense?

---

### Post by SagaciousKJB on 2018-09-19
I believe what you're looking for is...

```
ln -s /vmfs/volumes/55788775-1acaf4c1-37db-a46c2a38969e/scratch/log/syslog /var/log/syslog
```

That will make a symbolic link "syslog" in /var/log/ that points to /vmfs/volumes/55788775-1acaf4c1-37db-a46c2a38969e/scratch/log/syslog

Is this your only log file? Because perhaps you should use a mount --bind directive to mount the vmfs directory.

```
mount --bind /vmfs/volumes/55788775-1acaf4c1-37db-a46c2a38969e/scratch/log/ /var/log/
```

You can make such a rule in your /etc/fstab for that as well, but the only thing I'm not sure of is if the system will mount this bind directory before other services run and log to the real /var/log directory

Another solution might be simply to mount your volume's partition as the /var/log/ directory

```
mount /vmfs/volumes/55788775-1acaf4c1-37db-a46c2a38969e/scratch/log/ /var/log/
```

That way the filesystem should boot up and mount your partition to /var/log/ before other services log to the /var/log/ in the root directory.

---

