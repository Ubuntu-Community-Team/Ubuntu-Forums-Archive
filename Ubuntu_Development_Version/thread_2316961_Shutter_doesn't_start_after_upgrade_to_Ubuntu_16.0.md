---
title: "Shutter doesn't start after upgrade to Ubuntu 16.04"
date: 2016-03-12
forum: Ubuntu Development Version
---

### Post by sashhhh on 2016-03-12
I have upgraded to Ubuntu 16.04 and now Shutter won't work, and I really need that program at the moment. I tried reinstalling, after purging, but same thing. When started from the terminal, I get this:

"Can't use 'defined(@array)' (Maybe you should just omit the defined()?) at /usr/bin/shutter line 3727." 

I tried to search 'defined(@array)' in the file, but there is no such thing.

---

### Post by howefield on 2016-03-12
Moved to the "*Ubuntu Development Version*" forum.

Probably better searching for the full line, eg throws up this [launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/shutter/+bug/1532364").

---

### Post by v3.xx on 2016-03-12
Same error in Mate 16o4

---

### Post by kansasnoob on 2016-03-12
> I really need that program at the moment

This is why pre-releases aren't recommended for production machines. Breakage, both minor and major, is possible and sometimes quite frequent.

---

### Post by JMB74 on 2016-03-13
Version from the shutter ppa works here at least. Not tested the main archive version though.

```
apt-cache policy shutter
shutter:
  Installed: 0.93.1~ppa1~ubuntu16.04.1
  Candidate: 0.93.1~ppa1~ubuntu16.04.1
  Version table:
 *** 0.93.1~ppa1~ubuntu16.04.1 500
        500 http://ppa.launchpad.net/shutter/ppa/ubuntu xenial/main amd64 Packages
        500 http://ppa.launchpad.net/shutter/ppa/ubuntu xenial/main i386 Packages
        100 /var/lib/dpkg/status
     0.92-0.1ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial/universe i386 Packages


```

---

### Post by makitso on 2016-03-13
There is an old version in the repository, which I submitted a bug on.  To get shutter to work requires version 0.93.1, which you can get via their ppa.

sudo add-apt-repository ppa:shutter/ppa
sudo apt-get update
sudo apt-get install shutter

---

### Post by v3.xx on 2016-03-13
A PPA!  Good find, should of looked there, but I just assumed 16o4 had the latest and greatest.

Not going to test it any further; my mouse is trained to go to gimp :)

---

