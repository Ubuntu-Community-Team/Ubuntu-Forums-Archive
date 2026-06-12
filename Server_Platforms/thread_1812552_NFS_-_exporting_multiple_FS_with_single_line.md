---
title: "NFS - exporting multiple FS with single line?"
date: 2011-07-26
forum: Server Platforms
---

### Post by size_XXM on 2011-07-26
Hi,
I'm using my home server to [netboot into live CDs](https://wiki.edubuntu.org/LiveCDNetboot). To summarize that article, netbooting a liveCD system involves passing an NFS host:/path in kernel's command line, which is subsequently mounted as /cdrom on the live system. The article mentions copying the contents of the iso image to a place on the hard drive, but I see no reason for this, since the contents need to be read-only anyway, which is easy to achieve by mounting the iso through a loop device: ```
# mount
...
/dev/loop0 on /mnt/kubuntu-lucid-amd64 type iso9660 (ro)
/dev/loop1 on /mnt/kubuntu-natty-amd64 type iso9660 (ro)
/dev/loop2 on /mnt/kubuntu-natty-i386 type iso9660 (ro)
/dev/loop3 on /mnt/ubuntu-natty-i386 type iso9660 (ro)
```
Now, I am using NFS to mount a regular (rw, HDD) directory which I use as a network drive and I can mount any subdirectory and still access all the files within, ie. when I export /data on the server, I can still mount /data/downloads on the client:```
server:# exportfs
/data           192.168.1.4/32


client:$ sudo mount -t nfs 192.168.1.1:/data/downloads /mnt/netshare
client:$ ls -al /mnt/netshare
...{contents of /data/downloads follow}...
```

**_My question/problem is:_** Is it possible to export just /mnt and be able to mount any/all of the subdirectories? NFS doesn't like going across multiple file systems:```

server:# ls -al /mnt/kubuntu-natty-i386/
total 3532
dr-xr-xr-x 11 root root    4096 2011-04-27 11:29 .
drwxr-xr-x  7 root root    4096 2011-07-25 21:46 ..
-r--r--r--  1 root root     144 2011-04-27 11:27 autorun.inf
dr-xr-xr-x  3 root root    2048 2011-04-27 11:29 boot
dr-xr-xr-x  2 root root    2048 2011-04-27 11:29 casper
dr-xr-xr-x  2 root root    2048 2011-04-27 11:29 .disk
...
server:# exportfs
/mnt            192.168.0.0/16
...


client:$ sudo mount -t nfs 192.168.1.1:/mnt/kubuntu-natty-i386/ /tmp/nfsm/
client:$ ls -al /tmp/nfsm/
total 4
drwxr-xr-x  2 4294967294 4294967294 4096 2011-02-04 18:42 .
drwxrwxrwt 16 root       root        400 2011-07-26 19:20 ..
client:$ mount
...
192.168.1.1:/mnt/kubuntu-natty-i386/ on /tmp/nfsm type nfs (rw,vers=4,addr=192.168.1.1,clientaddr=192.168.1.4)
```When I try to export just /mnt and mount /mnt/kubuntu-natty-i386 on the client, the mount succeeds but the mounted directory is empty. Any ideas how/if this is possible? Or am I left to exporting each of /mnt/* individually?

---

### Post by size_XXM on 2011-07-26
To answer my own question, RingTFM (man exports) reveals the option "crossmnt" - just add it to options in /etc/exports, and voilà! :)
> crossmnt
              This  option  is similar to nohide but it makes it possible for clients to move from the filesystem marked with crossmnt to exported filesystems mounted on it.  Thus when a child filesystem "B" is mounted on a parent "A", setting crossmnt  on  "A" has the same effect as setting "nohide" on B.

---

