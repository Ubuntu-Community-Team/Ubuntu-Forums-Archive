---
title: "rdiff-backup giving Python errors"
date: 2021-09-25
forum: Server Platforms
---

### Post by aljames2 on 2021-09-25
Well I upgraded my desktop to 20.04.  My backup server is on 18.04 (headless server version)

My backup server pulls backups from the desktop.  Since the desktop upgrade, I am now getting python errors when running rdiff-backup.  I think it may have to do with the rdiff-backup versions available (which are different) in 20.04 & 18.04.  20.04 uses rdiff-backup 2.0.0, which requires and installs Python 3+ using apt.  While, 18.04 uses rdiff-backup 1.2.8 on Python 2+ and cannot be upgraded to 2.0.0 that I have found.  Perhapd I will have to upgrade the backup server to 20.04 in order to get same version running?

Found this resource:
[https://askubuntu.com/questions/1274699/need-to-try-to-install-a-specific-package-version-however-apt-cache-madison](https://askubuntu.com/questions/1274699/need-to-try-to-install-a-specific-package-version-however-apt-cache-madison)

---

### Post by TheFu on 2021-09-26
I ported the python2 version of rdiff-backup to my 20.04 system and installed it there.  My backup server runs 18.04 too.  
```
$ rdiff-backup --version
rdiff-backup 1.2.8

$ file /usr/local/bin/rdiff
/usr/local/bin/rdiff: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=37a8ca37e600fd98526c93bad8e5657e10106822, for GNU/Linux 3.2.0, with debug_info, not stripped
$ rdiff --version
rdiff (**librsync** 0.9.7) [x86_64-unknown-linux-gnu]
Copyright (C) 1997-2001 by Martin Pool, Andrew Tridgell and others.
http://rproxy.samba.org/
Capabilities: 64 bit files

$ locate librsync
/usr/local/include/librsync-config.h
/usr/local/include/librsync.h
/usr/local/lib/librsync.a
/usr/local/lib/librsync.la
/usr/local/lib/python2.7/dist-packages/rdiff_backup/_librsync.so
/usr/local/lib/python2.7/dist-packages/rdiff_backup/librsync.py
/usr/local/lib/python2.7/dist-packages/rdiff_backup/librsync.pyc
/usr/local/share/man/man3/librsync.3
```

rdiff-backup is python2, so there's no way around installing that dependency.

Think I had to recompile librsync and rdiff (not rdiff-backup) too, but I don't recall. Sorry.

BTW, the file format on disk hasn't changed, the problem is that rdiff-backup is dependent on the python serialization of data between the client and the server.  Python3 changed it from python2. They are incompatible.

Good news. I took some notes in vimwiki for copying my port to other systems:

== 20.04 rdiff-backup Install ==

```
sudo apt install python2

# Install rdiff scripts - running in root account
cd /usr/local/bin/
scp thefu@regulus:/usr/local/bin/rdiff* .

# Get librsync stuff  - running in root account
cd /usr/local/lib
scp thefu@regulus:/usr/local/lib/librsync.* .

# Get librsync stuff - python2 modules  - running in root account
cd python2.7/dist-packages/
rsync -avz regulus:/usr/local/lib/python2.7/dist-packages/rdiff_backup .
```

I'm positive these steps work to copy the stuff to other systems, since I moved my email gateway over to 20.04 last month and setup "pull" backups for it from an 18.04 server.  I didn't re-port librsync or rdiff, so those steps aren't available. I don't recall them being too hard.   regulus is the 20.04 client system where I did the original porting. ;)

20.04 and later OSes are python3.  There are a number of workarounds besides porting. You could setup a 20.04 lxd container with access to the backup storage on your backup server, then using that to service all 20.04 client machines and use the current 18.04 server for earlier clients.  I've considered this myself.  Or work out a plan to migrate to a new 20.04 backup server (perhaps with a different, newer, HDD).  Setup and use of LXD is crazy fast. The minimal OS is under 2G, just hook up some storage.  Of course, lxd is provided only as a snap package, which breaks on most of my systems due to my use of NFS for HOME directories. For a 20.04 backup server, I wouldn't need that.

You know.  Think I'll setup that 20.04 lxd server now on the 18.04 backup server.  I'll take some notes.
```
$ sudo snap install lxd
$ lxd init <--- the questions here are a little funky.  It never asked me about storage, which is scary. I did have to setup a local userid, no NFS home.  Hooked up the network bridge to an existing bridge on the system, so it will have an IP on that same subnet.
$ lxc list   <--- shows nothing.
$ lxc launch ubuntu:20.04 back-2004    <--- that downloads and creates the 20.04 system.
$ lxc list
+-----------+---------+----------------------+------+-----------+-----------+
|   NAME    |  STATE  |         IPV4         | IPV6 |   TYPE    | SNAPSHOTS |
+-----------+---------+----------------------+------+-----------+-----------+
| back-2004 | RUNNING | 172.22.22.231 (eth0) |      | CONTAINER | 0         |
+-----------+---------+----------------------+------+-----------+-----------+
$ lxc exec  back-2004 -- sudo --login --user ubuntu
**# Now on the new LXD system:**
$ df -Th -x tmpfs
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdc1      ext4       20G   12G  6.7G  64% /

```

Looks good, but I don't like the default storage under /var/lxd/ .  Really want to put that on some RAID1 storage this machine has.  Need to move the networking over to a static IP, update DNS, setup ssh-server, rdiff-backup, .... hook up some nfs storage to the main backup server storage locations. It is a hack for now.
Not bad for 10 minutes.

---

### Post by TheFu on 2021-09-26
NFS as a client (or a server) is problematic for LXD.  Should have known.  I need to sleep on it.  Seems that running an unprivileged lxd container and using NFS isn't possible.  Unprivileged containers are a key aspect for security. Here's a discussion: 
[https://github.com/lxc/lxd/issues/1826](https://github.com/lxc/lxd/issues/1826)

Just tested the solution.  Shutdown the container, then run (from the container host system)
```
$ lxc config set back-2004 raw.apparmor "mount fstype=nfs,"
$ lxc config set back-2004 security.privileged true
```

And because these are for backups, you'll probably want to put _**no_root_squash**_ as an option in the /etc/exports NFS config file. Ouch. Lots of not-so-great security choices here, but the no_root_squash was going to be required, regardless with any NFS storage accessed for backups. Just be certain to lock down the NFS export to just the NFS client that needs it, not the entire subnet.  Being lazy with nfs exports is always a security issue.

---

### Post by aljames2 on 2021-09-26
It’s good to see that rdiff-backup is being actively maintained once again.  In my case, it may be simpler to upgrade my backup server since I don’t maintain any earlier release systems now.  Thanks for the details and providing the port over steps!

---

### Post by TheFu on 2021-09-26
> **aljames2 said:**
> It’s good to see that rdiff-backup is being actively maintained once again.  In my case, it may be simpler to upgrade my backup server since I don’t maintain any earlier release systems now.  Thanks for the details and providing the port over steps!

Beware of some things that are still breaking in 20.04 which could be very important.  There are lots of issues with NFS, it seems. I spent the last 45 min trying to setup an NFS server on 20.04 and failed.  Got passed a few issues, then hit a road block I can't seem to solve and haven't found a solution online.

---

### Post by TheFu on 2021-09-29
Thought I should post this.  The 20.04 NFS client is working, even under LXD.  

The fstab line on the client:
```
romulus:/Data/1.5T/Backups /Backups nfs    defaults    0 0
```

The /etc/exports line on the server:
```
/Data/1.5T 172.22.22.16(fsid=6,rw,async,no_root_squash,no_subtree_check)
```

The client IP is 172.22.22.16.  "romulus" is in my LAN DNS, so always found.  Root/sudo from the client can write to the storage - that's what the no_root_squash option does. I feel a little dirty using it, but for this purpose, it seems reasonable and that storage is only shared out to a 20.04 backup server from an 18.04 backup server. Actually, the lxd container is running on the 18.04 backup server, so NFS traffic should all be within the same machine and probably at 15+Gbps.   Yep. ~ 20Gbps. Good enough.
```
$ iperf3 -c romulus
Connecting to host romulus, port 5201
[  5] local 172.22.22.16 port 51114 connected to 172.22.22.4 port 5201
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec  2.25 GBytes  19.3 Gbits/sec    0    392 KBytes       
[  5]   1.00-2.00   sec  2.34 GBytes  20.1 Gbits/sec    0    417 KBytes       
[  5]   2.00-3.00   sec  2.32 GBytes  20.0 Gbits/sec    0    417 KBytes   
```

When any other system attempts to mount it:
```

$ sudo mount -t nfs romulus:/Data/1.5T/Backups /Backups 
mount.nfs: access denied by server while mounting romulus:/Data/1.5T/Backups
```

Sometimes when NFSv4 isn't working, adding the fsid= option makes all the difference.

---

### Post by rsteinmetz70112 on 2021-09-29
You hace a server named romulus? I also have remus. The are a pair with slightly different tasks.

---

### Post by aljames2 on 2021-10-02
Thanks again TheFu!  I did an upgrade on my simple backup server.  I didn't have much at stake with just a few desktops that I upgraded to 20.04 a while back.  rdiff-backup 2.0 works without a hitch for me now.  However, I am now going to use some of your info here to set up an LXD container on the 20.04 backup server and play around with NFS.  

What I am imagining is use the LXD container as an NFS server.  It would read-only from some data on one of the backup drives, and then the desktops could use NFS to read-only from the NFS server.  Not sure if I am theorizing correctly how this is supposed to work, but this is what I'm after, or something like it. O:)

---

### Post by TheFu on 2021-10-02
There are "complications" when using NFS inside an lxd container, I've learned.  You might want to seek alternative modes.
I wasn't able to get the NFS-server working. I did get an NFS client working inside an lxd container. I'm rethinking my use ... for direct storage sharing via lxd capabilities to storage on the LXD host. Came across an lxc container setting to support this, but haven't tried it. Running a container in privileged mode, as is required for NFS to work, is just wrong, especially when there is another alternative.

[https://askubuntu.com/questions/691039/adding-a-shared-host-directory-to-an-lxc-lxd-container](https://askubuntu.com/questions/691039/adding-a-shared-host-directory-to-an-lxc-lxd-container)
> Mount the host folder /var/www as /var/test in the container.

$ lxc config device add mycontainer vartest disk source=/var/www path=/var/test

And this: [https://discuss.linuxcontainers.org/t/share-folder-between-containers/7126](https://discuss.linuxcontainers.org/t/share-folder-between-containers/7126)

---

