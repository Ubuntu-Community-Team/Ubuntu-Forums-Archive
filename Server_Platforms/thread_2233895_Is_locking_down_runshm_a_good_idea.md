---
title: "Is locking down /run/shm a good idea?"
date: 2014-07-11
forum: Server Platforms
---

### Post by RavenLX on 2014-07-11
I came across this: [https://help.ubuntu.com/community/StricterDefaults](https://help.ubuntu.com/community/StricterDefaults) 

 I am running Ubuntu servers of various flavors (10.04 which we hope to move to 14.04). These are used as web servers for hosting things like Wordpress, CMS, forums, CGI scripts, custom php sites, etc. Is this a good idea to add to /etc/fstab?

  ```
tmpfs     /run/shm     tmpfs     rw,noexec,nosuid,nodev     0     0
``` 
(In 14.04 it's /run/shm, btw. 

Didn't check what it was in 10.04, but may be /dev/shm). I don't want to risk functionality of web sites but I do want to do what I can to prevent sites from being hacked.

---

### Post by Gyokuro on 2014-07-11
Hi

I would say go ahead and the only thing I can add is that you maybe limit it's size as the default is to use half of your system memory. If you know how much shm memory is needed you can append 

**size**=1620720k

and another thing is I mount it with an additional **relatime **.

- HTH

---

### Post by RavenLX on 2014-07-11
Thank you for the advice. So if I am understanding you right, the line to add to /etc/fstab would be (as an example):

```
tmpfs     /run/shm     tmpfs     rw,noexec,nosuid,nodev,realtime     0     0        size=1620720k
```

---

### Post by Gyokuro on 2014-07-12
Hi

you have a typo and your tmpfs fstab line should be: 

tmpfs     /run/shm     tmpfs     rw,noexec,nosuid,nodev,relatime,size=1620720k     0     0

- HTH

---

### Post by RavenLX on 2014-07-15
Thank you for the correction. At first I thought "relatime" was a typo and thought it was to be "realtime". I also wasn't sure where to put "size". I copied your code down in my notes so that I have the correct information to update the configuration with.

---

