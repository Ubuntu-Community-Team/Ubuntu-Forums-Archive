---
title: "no space left on device"
date: 2009-08-24
forum: Server Platforms
---

### Post by and12345 on 2009-08-24
when i try to updating my ubuntu server (9.04) i got no space left on device error... i don't know why because 1 see my sda1 still got 1.3G free..
this error freaking me out coz i can't do anything with my proxy server (even SARG can't generate report)

when i run df -h the output is

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.7G  2.3G  1.3G  65% /
varrun                252M  184K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   64K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
/dev/sda6             3.9G  146M  3.6G   4% /home
/dev/sdc1             3.9G  3.4G  338M  92% /hdd3/partition1
/dev/sdc2             4.1G  3.5G  417M  90% /hdd3/partition2

need your help guys :confused:

---

### Post by nandemonai on 2009-08-24
devshm 252M 0 252M 0% /dev/shm <- Your tmp FS is full. Is the machine out of RAM / SWAP space?

I'm thinking that's your problem.

Post the output from:

```
free -m
```

---

### Post by and12345 on 2009-08-24
```

     total         used       free     shared    buffers     cached
Mem:   503          496          7          0        154         86
-/+ buffers/cache:  255        248
Swap:  400            0        399

```

yes... i see my memory is full and my swap is free, how do i free up my memory?
is this normally happened on ubuntu?

---

### Post by nandemonai on 2009-08-25
Hmm, that's odd. It should be using the swap if your RAM is full. Not too sure what to tell you.

Hate to suggest it but a reboot might be worth while. Unless someone else can chime in with a better suggestion. :confused:

---

### Post by and12345 on 2009-08-28
already try reboot but still no solution

---

