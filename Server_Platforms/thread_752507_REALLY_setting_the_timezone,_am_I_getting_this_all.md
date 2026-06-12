---
title: "REALLY setting the timezone, am I getting this all wrong"
date: 2008-04-11
forum: Server Platforms
---

### Post by aktxyz on 2008-04-11
We have a virtual appliance running Gutsy server that was setup with UTC in the CST timezone.

When we deploy this server into the PST timezone, we'd like the change the timezone of the server.

I have edited the /etc/timezone file to contain America/Los_Angeles, just like tzselect told me to do.

Now when I log in or su to root, it still shows the old time/timezone.  I know I can add a TZ var to my environment, but I also want root to know this machine is in PST.  

It seems like the system still thinks it is in CST and not PST.  How do I REALLY change the timezone??

Or am I just thinking about this all wrong?

---

### Post by songshu on 2008-04-12
tzselect?

---

### Post by gombadi on 2008-04-12
/etc/localtime is the file you want.

On mine it is a sym link to the actual zone file.

```

user@machine:~$ ls -l /etc/localtime 
lrwxrwxrwx 1 root root 36 2008-03-30 09:34 /etc/localtime -> /usr/share/zoneinfo/Australia/Sydney

```

As root type -
```

mv /etc/localtime /etc/localtime.orig
ln -s /usr/local/zoneinfo/America/Los_Angeles /etc/localtime

```

---

