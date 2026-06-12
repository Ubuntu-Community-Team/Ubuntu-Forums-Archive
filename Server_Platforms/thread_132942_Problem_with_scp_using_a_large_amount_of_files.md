---
title: "Problem with scp using a large amount of files"
date: 2006-02-19
forum: Server Platforms
---

### Post by spartas on 2006-02-19
I'm trying to copy my home partition on a machine running Dapper to my file server which is running breezy.  The copy gets through a large amount of files successfully and then starts returning 'No space left on device' errors on the server.

On the client I'm using an i386 dapper install (which may be the problem, but I don't konw yet), with /home on an ext3 filesystem separate from /.

My file server is running an AMD64 breezy install (Xeon 64-bit processor), using LVM on the / and /home partitions.  /home is made up of a RAID5 array using 4 74Gig drives, which should yield me about 222Gb.

Here's the output of several commands.

First, the command I used to copy
```

tim@epiphany:~ $ scp -r * tim@Asynjur:~/epiphany/

```

The last file that copied successfully, followed by the first file that failed.
```

base3.xcf                                     100%  427     0.4KB/s   00:00
scp: /home/tim/epiphany//hidden-dapper/.themes/H2O-gtk2-Amythist/gtk-2.0/.xvpics/sup2.png: No space left on device

```

The output of df on the server
```

tim@asynjur:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/Ubuntu-root
                       33G  1.7G   29G   6% /
tmpfs                1003M     0 1003M   0% /dev/shm
tmpfs                1003M   14M  989M   2% /lib/modules/2.6.12-10-amd64-generic/volatile
/dev/sda1             228M   22M  195M  10% /boot
/dev/mapper/array-home
                      196G   51G  146G  26% /home

```

Finally, what happens when I try to create files on the server:
```

tim@asynjur:~$ touch me
touch: cannot touch `me': No space left on device

```

---

### Post by drogoh on 2006-02-19
What I would suggest is, instead of copying all of those individual files and potentially using up all of your inodes, tar it all up and scp that one file over.

---

### Post by LordHunter317 on 2006-02-19
That won't solve the problem when he untars.

Output of df -i?  And this is to /home, not /, right?  Your / is full and only root will be able to put more data there.

---

### Post by spartas on 2006-02-19
Actually I'm only using 6% of /
/ is on its own drive (a 37.5G drive)

But, yes I am using /home to store the files.


Also, I've noticed some of the files in my client home dir are owned by root.  I'm not sure if this will have any effect on the scp process.


I'll post the output of df -i when I can.

---

### Post by Strife on 2006-02-19
That's odd. I've noticed that scp seems to behave kinda weirdly if you're trying to copy multiple files at once sometimes. Have you given rsync a try?

---

### Post by spartas on 2006-02-19
I'm fairly sure that i'm using up all the inodes on the server.  Before the copy, I'm using 28% of the inodes.
```

tim@asynjur:~/public_html/wp$ df -hi
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/mapper/Ubuntu-root
                        4.2M     63K    4.1M    2% /
tmpfs                   251K       1    251K    1% /dev/shm
tmpfs                   251K      13    251K    1% /lib/modules/2.6.12-10-amd64-generic/volatile
/dev/sda1               122K      39    122K    1% /boot
/dev/mapper/array-home
                         49K     14K     36K   28% /home

```

I'm currently running the scp again to get the files back on the server, but here's what it looks like now.  It's still working on the hidden files in the /home directory on the client.

```

tim@asynjur:~/epiphany$ df -ih
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/mapper/Ubuntu-root
                        4.2M     63K    4.1M    2% /
tmpfs                   251K       1    251K    1% /dev/shm
tmpfs                   251K      13    251K    1% /lib/modules/2.6.12-10-amd64-generic/volatile
/dev/sda1               122K      39    122K    1% /boot
/dev/mapper/array-home
                         49K     38K     12K   76% /home

```

This is meant to be a file server, and currently I have about 40Gigs of music on there right now.

---

### Post by spartas on 2006-02-19
Predictably, it started throwing those 'No space left on device' errors when the inodes went to zero.  Is there a way to increase the amount of inodes available on /home?  

```

tim@asynjur:~/epiphany$ df -hi
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/mapper/Ubuntu-root
                        4.2M     63K    4.1M    2% /
tmpfs                   251K       1    251K    1% /dev/shm
tmpfs                   251K      13    251K    1% /lib/modules/2.6.12-10-amd64-generic/volatile
/dev/sda1               122K      39    122K    1% /boot
/dev/mapper/array-home
                         49K     49K       0  100% /home

```

I have 4.2M inodes total in /, but only 49K on home.  What?

---

### Post by spartas on 2006-02-21
Okay, so this system doesn't have enough inodes on the /home partition, however, it has 4.2M on the / partition.  Hmmm.  Is reformatting using ext3 with -N [nodes] the best way to fix this, or should I consider using a different filesystem?  I am using this as my fileserver, and I would like it to be reliable (so no dangerous sorcery magic).  I have tarred the /home partition to a seperate file somewhere else so I can reformat, but what is the best approach from here?

---

