---
title: "No Disk Space left on drive /"
date: 2009-04-20
forum: Server Platforms
---

### Post by mitanc on 2009-04-20
Hey All,

About a month ago I installed a new ubuntu intrepid server in my office.  There are two issues I am having:

1.  During bootup I always get jumped into recovery mode, one of my partitions which is the file server is having errors.  fsck automatically runs, then it kicks me out to the terminal and says to run it manually.  I do that, fix a bunch of errors (clear inodes, etc.) but at reboot the problems occur again.  I recently did it and lost a bunch of files on my file server.

2.  The root (/) partition is shows as full.  I have 2 GB in there and know for a fact it can't be full.  Here is an output of my parition table

```
root@dc01-lg:/# df -ah
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/ddf1_4c53492020202020808626820000000036e018a500000a285
                      1.9G  1.9G     0 100% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
/proc                    0     0     0   -  /proc
sysfs                    0     0     0   -  /sys
varrun                2.0G  1.1M  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  2.9M  2.0G   1% /dev
fusectl                  0     0     0   -  /sys/fs/fuse/connections
/dev/mapper/ddf1_4c53492020202020808626820000000036e018a500000a281
                       92M   18M   69M  21% /boot
/dev/mapper/ddf1_4c53492020202020808626820000000036e018a5000014501
                      4.6G  141M  4.3G   4% /home
/dev/mapper/ddf1_4c53492020202020808626820000000036e018a5000014505
                       92G   12G   76G  14% /ldapdata
/dev/mapper/ddf1_4c53492020202020808626820000000036e018a500000a289
                       46G  180M   44G   1% /mnt/backup
/dev/mapper/ddf1_4c53492020202020808626820000000036e018a500000a287
                      942M   18M  877M   2% /tmp
/dev/mapper/ddf1_4c53492020202020808626820000000036e018a500000a286
                      4.6G  695M  3.7G  16% /usr
/dev/mapper/ddf1_4c53492020202020808626820000000036e018a500000a288
                      1.9G  273M  1.5G  16% /var
rpc_pipefs               0     0     0   -  /var/lib/nfs/rpc_pipefs
securityfs               0     0     0   -  /sys/kernel/security
nfsd                     0     0     0   -  /proc/fs/nfsd

```

And this is the output of 
```
du * -s | sort -nr | head
11628816 ldapdata
1750680 ldapbackup
570260 usr
246320 var
111624 lib
12377 boot
7484 etc
6988 sbin
4820 bin
```

I have have 2 160 GB drivers in software raid setup to hold my OS and I have two 500 GB drives to hold my data (/ldapdata and /ldapbackup) 

I could use all the help I could, thanks so much.

---

### Post by mitanc on 2009-04-20
Okay, I figured out the issue with my server.  I had a fakeraid installed onto the server but I had disabled the bios hardware controller.  This in turn ruined the configuration.  Anyways, thanks for all who viewed :-)

---

