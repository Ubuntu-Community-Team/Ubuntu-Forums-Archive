---
title: "mount command"
date: 2011-09-15
forum: Server Platforms
---

### Post by mbaker2311 on 2011-09-15
I want to virtualize some Ubuntu servers.  To do this accurately, I need to know how much local storage each machine has.  Is there a command, or command and parameters, that I can run that will tell me how much total local storage there is on the system, and how much is being used (or how much is free?)  I'm thinking something like the Computer Management screen in Windows, under Disk Management.  When I run the mount command, I get no info, and it also reports on remotely mounted storage.

---

### Post by rubylaser on 2011-09-15
This will show you used and available easily.
```
df -h
```

Like this...
```
root@svr-cc-marketing:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/cciss/c0d0p1      46G  2.4G   42G   6% /
none                  4.0G  212K  4.0G   1% /dev
none                  4.0G     0  4.0G   0% /dev/shm
none                  4.0G   19M  3.9G   1% /var/run
none                  4.0G     0  4.0G   0% /var/lock
none                  4.0G     0  4.0G   0% /lib/init/rw
none                   46G  2.4G   42G   6% /var/lib/ureadahead/debugfs
/dev/cciss/c0d0p3     901G  479G  422G  54% /var/marketing
```

---

### Post by papibe on 2011-09-15
If you are looking for a simple command to see how full (or empty) is your mounted hard drives, you can use 'df'.

Use it like this
```
$ df -h
```
I like to use the -h option so the amounts are displayed in 'human' abbreviations.

This is an example of the output look:
```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             9.4G  6.2G  2.8G  69% /
none                  2.0G  388K  2.0G   1% /dev
none                  2.0G  320K  2.0G   1% /dev/shm
none                  2.0G  352K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda6              94G   34G   56G  38% /home
/dev/sdb1             932G  835G   97G  90% /media/My Book
/dev/sdc1             932G  800G  133G  86% /media/Iomega

```
You can use partition names as parameters. For example:
```
$ df -h /
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             9.4G  6.2G  2.8G  69% /

```
In order the do some automation by using df, you will need some scripting. Here's a simple example on how to get the availble space on the root partition.
```
#!/bin/bash
part="/"

available=$(df "$part"| tail -n +2 | awk '{print $4}')

echo "There is "$available" free space on partition "$part""
```

Hope it helps,
Regards.

---

