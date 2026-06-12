---
title: "help with disk usage"
date: 2010-10-20
forum: Server Platforms
---

### Post by plablo09 on 2010-10-20
Hello I'm experiencing a strange problem on a ubuntu 9.10 server.
The problem is that when I try to mkdir in /var/local/ it says th disk is full but running df -h outputs:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              15G  5.0G  9.2G  36% /
udev                  982M  156K  981M   1% /dev
none                  982M     0  982M   0% /dev/shm
none                  982M  312K  981M   1% /var/run
none                  982M     0  982M   0% /var/lock
none                  982M     0  982M   0% /lib/init/rw
/dev/sda5              42G  3.3G   36G   9% /home
/dev/sda6              89G   32G   53G  38% /var
```

I have 53G available on /var!
I cannot see what's eating up my space in /var, any help is appreciated
regards
Pablo

---

### Post by CharlesA on 2010-10-20
Try this:

```
du -h --max-depth=1 /var
```

---

### Post by plablo09 on 2010-10-20
Thanks for your answer CharlesA, here's the output from du -h --max-depth=1 /var:

```
12K     /var/mail
4.4M    /var/backups
263M    /var/tile_temp
2.1G    /var/log
0       /var/lock
316K    /var/run
4.0K    /var/opt
36K     /var/spool
4.0K    /var/crash
142M    /var/cache
16K     /var/lost+found
23G     /var/tile_geoserver_tmp
2.1G    /var/lib
12K     /var/local
388K    /var/tmp
4.5G    /var/www
32G     /var
```

I still cant see where the disk space is going

---

### Post by CharlesA on 2010-10-20
Can you post the exact error that you are getting?

Put the whole output in code tags please. :)

---

### Post by plablo09 on 2010-10-20
Ok, here's the code:
```
plablo@geoweb:/var/local$mkdir something
mkdir: cannot create directory `something': No space left on device

```

---

### Post by CharlesA on 2010-10-20
I found some info [here]("http://www.linuxquestions.org/questions/linux-general-1/cp-no-space-left-on-device-but-df-does-not-agree-21996/").

Best thing to do would be to run fsck on that device, to rule out file system corruption.

---

### Post by plablo09 on 2010-10-20
Ok, I will do that after running a couple of backups and report back
Thanks a lot

---

### Post by dtfinch on 2010-10-20
> 23G     /var/tile_geoserver_tmpThat might be part of it.

---

### Post by CharlesA on 2010-10-20
> **dtfinch said:**
> That might be part of it.

The drive still has free space according to df, so I doubt that's the problem.

---

### Post by plablo09 on 2010-10-20
> **dtfinch said:**
> That might be part of it.

Not really, thats expected and it's part of the 32G listed in /var

---

### Post by brettg on 2010-10-20
It appears that you might be running a webserver here. 

Do this;

```
lsof /var/tmp
```

I know it sounds strange but if you see a large volume of files here try restarting apache and let me know what happens.

---

### Post by plablo09 on 2010-10-21
> **CharlesA said:**
> I found some info [here]("http://www.linuxquestions.org/questions/linux-general-1/cp-no-space-left-on-device-but-df-does-not-agree-21996/").

Best thing to do would be to run fsck on that device, to rule out file system corruption.

Well, I finally had time to do this with:
```
shutdown -rF
```
fsck didnt complain on boot, but nothing was written to the logs and the problem persisted. I'm thinking that fsck could have exited with some error due to this but I'm not shure.

I'm gonna try to run fsck from a livecd to see whats going on
Thanks

---

### Post by plablo09 on 2010-10-21
> **brettg said:**
> It appears that you might be running a webserver here. 

Do this;

```
lsof /var/tmp
```

I know it sounds strange but if you see a large volume of files here try restarting apache and let me know what happens.

Well, ```
lsof /var/tmp
``` returns nothing

---

### Post by iponeverything on 2010-10-21
you probably ran out of inodes.


run:
```

df -i 
```

---

### Post by plablo09 on 2010-10-21
> **iponeverything said:**
> you probably ran out of inodes.


run:
```

df -i 
```

Ok, that's right on!
I've found the culprit, a script was generating way more tiles than needed
Thanks a lot everyboy for your help!

---

