---
title: "Disk not unmounting cleanly on reboot"
date: 2011-06-15
forum: Server Platforms
---

### Post by zigsterabg on 2011-06-15
Hi,

We are using Ubuntu 10.04LTS server on Vmware Vsphere estate.  We are using LVM and have / and /var on separate partitions.

We have been experiencing an odd issue with sda1 always being fsck'd after every reboot.  We seem to have traced this to the start/kill scripts in rc0.d and rc6.d.  It appears that the reason the disk is not being unmounted is because some of the scripts are never being run because they are prefixed with S.  We renamed and reordered the scripts to reflect what we thought should be the correct order - i.e. not halting the system before unmounting disks.  System reboots cleanly now.

Before list of rc0.d and rc6.d respectively:
lrwxrwxrwx  1 root root   17 2010-11-18 15:06 K01apache2 -> ../init.d/apache2
lrwxrwxrwx  1 root root   22 2010-11-16 17:03 K01zabbix-agent -> ../init.d/zabbix-agent
lrwxrwxrwx  1 root root   22 2010-11-30 08:16 K03vmware-tools -> ../init.d/vmware-tools
lrwxrwxrwx  1 root root   14 2010-11-16 17:03 S01halt -> ../init.d/halt
lrwxrwxrwx  1 root root   18 2010-11-16 17:03 S01sendsigs -> ../init.d/sendsigs
lrwxrwxrwx  1 root root   18 2010-11-16 17:03 S01umountfs -> ../init.d/umountfs
lrwxrwxrwx  1 root root   22 2010-11-16 17:03 S01umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx  1 root root   20 2010-11-16 17:03 S01umountroot -> ../init.d/umountroot
lrwxrwxrwx  1 root root   20 2010-11-30 08:16 S02networking -> ../init.d/networking
lrwxrwxrwx  1 root root   17 2010-11-16 17:03 S02urandom -> ../init.d/urandom

lrwxrwxrwx  1 root root   17 2010-11-18 15:06 K01apache2 -> ../init.d/apache2
lrwxrwxrwx  1 root root   22 2010-11-16 17:03 K01zabbix-agent -> ../init.d/zabbix-agent
lrwxrwxrwx  1 root root   22 2010-11-30 08:16 K03vmware-tools -> ../init.d/vmware-tools
lrwxrwxrwx  1 root root   16 2010-11-16 17:03 S01reboot -> ../init.d/reboot
lrwxrwxrwx  1 root root   18 2010-11-16 17:03 S01sendsigs -> ../init.d/sendsigs
lrwxrwxrwx  1 root root   18 2010-11-16 17:03 S01umountfs -> ../init.d/umountfs
lrwxrwxrwx  1 root root   22 2010-11-16 17:03 S01umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx  1 root root   20 2010-11-16 17:03 S01umountroot -> ../init.d/umountroot
lrwxrwxrwx  1 root root   20 2010-11-30 08:16 S02networking -> ../init.d/networking
lrwxrwxrwx  1 root root   17 2010-11-16 17:03 S02urandom -> ../init.d/urandom

After list of rc0.d and rc6.d respectively:
lrwxrwxrwx 1 root root  17 2010-11-18 15:06 K01apache2 -> ../init.d/apache2
lrwxrwxrwx 1 root root  13 2010-11-22 11:53 K01ece -> ../init.d/ece
lrwxrwxrwx 1 root root  19 2011-01-21 14:08 K01memcached -> ../init.d/memcached
lrwxrwxrwx 1 root root  15 2010-11-16 17:03 K01slapd -> ../init.d/slapd
lrwxrwxrwx 1 root root  17 2010-11-16 17:03 K01urandom -> ../init.d/urandom
lrwxrwxrwx 1 root root  22 2010-11-16 17:03 K01zabbix-agent -> ../init.d/zabbix-agent
lrwxrwxrwx 1 root root  20 2010-11-30 08:16 K02networking -> ../init.d/networking
lrwxrwxrwx 1 root root  22 2010-11-30 08:16 K03vmware-tools -> ../init.d/vmware-tools
lrwxrwxrwx 1 root root  18 2010-11-16 17:03 K05sendsigs -> ../init.d/sendsigs
lrwxrwxrwx 1 root root  22 2010-11-16 17:03 K10umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx 1 root root  18 2010-11-16 17:03 K20umountfs -> ../init.d/umountfs
lrwxrwxrwx 1 root root  20 2010-11-16 17:03 K30umountroot -> ../init.d/umountroot
lrwxrwxrwx 1 root root  14 2010-11-16 17:03 K99halt -> ../init.d/halt

lrwxrwxrwx 1 root root  17 2010-11-18 15:06 K01apache2 -> ../init.d/apache2
lrwxrwxrwx 1 root root  13 2010-11-22 11:53 K01ece -> ../init.d/ece
lrwxrwxrwx 1 root root  19 2011-01-21 14:08 K01memcached -> ../init.d/memcached
lrwxrwxrwx 1 root root  15 2010-11-16 17:03 K01slapd -> ../init.d/slapd
lrwxrwxrwx 1 root root  17 2010-11-16 17:03 K01urandom -> ../init.d/urandom
lrwxrwxrwx 1 root root  22 2010-11-16 17:03 K01zabbix-agent -> ../init.d/zabbix-agent
lrwxrwxrwx 1 root root  20 2010-11-30 08:16 K02networking -> ../init.d/networking
lrwxrwxrwx 1 root root  22 2010-11-30 08:16 K03vmware-tools -> ../init.d/vmware-tools
lrwxrwxrwx 1 root root  18 2010-11-16 17:03 K05sendsigs -> ../init.d/sendsigs
lrwxrwxrwx 1 root root  22 2010-11-16 17:03 K10umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx 1 root root  18 2010-11-16 17:03 K20umountfs -> ../init.d/umountfs
lrwxrwxrwx 1 root root  20 2010-11-16 17:03 K30umountroot -> ../init.d/umountroot
lrwxrwxrwx 1 root root  16 2010-11-16 17:03 K99reboot -> ../init.d/reboot
(There is a mismatch between number of scripts before and after just because we loaded some extra stuff in between all of this happening.)

We must be missing something here because I cannot believe this is how it should be.  By default the system should shut down cleanly at the very least.  I understand that Ubuntu uses a mix of Upstart as well as SysV.

Most of the scripts have the following in it which, if I have not misunderstood things, tells it whether to run or not:
case "$1" in
  start)
        # No-op
        ;;
  restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
  stop)
        do_stop
        ;;
  *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
As, most have S prefix they do not run.  As already mentioned, when we change prefix to K all is well.

Apologies for long post but trying to get all info in - basically are we expected to do these changes as part of building new servers for production use?  Quite happy to do this but just surprised that this is the default.

Thanks in advance.

Andrew

---

### Post by ruffEdgz on 2011-06-15
Just to point out what I see that is wrong in both rc0.d and rc6.d (respectively) are these lines:
```
lrwxrwxrwx 1 root root 14 2010-11-16 17:03 S01halt -> ../init.d/halt
```
```
lrwxrwxrwx 1 root root 16 2010-11-16 17:03 S01reboot -> ../init.d/reboot
```
On some of the servers that I have at my work, both of these scripts are running S90, not S1. I believe that maybe the real reason why your disk is doing an fsck every time because it halts or reboots the machine before completing the rest of the scripts that help unmount the file system:
```

lrwxrwxrwx 1 root root 18 2010-11-16 17:03 S01umountfs -> ../init.d/umountfs
lrwxrwxrwx 1 root root 22 2010-11-16 17:03 S01umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx 1 root root 20 2010-11-16 17:03 S01umountroot -> ../init.d/umountroot

```

Below is an example of a Ubuntu 10.04 server I work on the order of operations when it comes to rc6.d (you can also take this example for rc0.d as well but replace reboot with halt):
```

lrwxrwxrwx  1 root root   18 2010-07-08 15:23 S20sendsigs -> ../init.d/sendsigs*
lrwxrwxrwx  1 root root   17 2010-07-08 15:23 S30urandom -> ../init.d/urandom*
lrwxrwxrwx  1 root root   22 2010-07-08 15:23 S31umountnfs.sh -> ../init.d/umountnfs.sh*
lrwxrwxrwx  1 root root   20 2010-07-08 15:23 S35networking -> ../init.d/networking*
lrwxrwxrwx  1 root root   18 2010-07-08 15:23 S40umountfs -> ../init.d/umountfs*
lrwxrwxrwx  1 root root   20 2010-07-08 15:23 S60umountroot -> ../init.d/umountroot*
lrwxrwxrwx  1 root root   16 2010-07-08 15:23 S90reboot -> ../init.d/reboot*

```

I don't know why placing the K prefix on everyone in your rc#.d would help but that probably isn't the best thing to do ;)

---

### Post by zigsterabg on 2011-06-16
Hi,

Thanks for the reply.

My issue is that, by default, an Ubuntu system will not boot cleanly because the scripts to unmount the fs are never called because it is prefixed with an S.  My understanding of SysV is that when you request a reboot it will run all the scripts prefixed with a K.  As the scripts are prefixed with an S they are never called.

What I am not sure about is whether this is default behaviour and we are expected to meddle with these files to do what we want.  I'm more experienced with Solaris and generally never have to meddle with these files.

Any ideas?  Also, it upstart supposed to deal with some of this?

Andrew

---

### Post by drei666 on 2011-09-15
Hi all,
I have Kubuntu 11.04 and I solved the problem just renaming 2 files:

1. rename /etc/rc0.d/S03halt in /etc/rc0.d/S99halt (takes care of shutdown)
2. rename /etc/rc6.d/S03reboot in /etc/rc6.d/S99reboot (takes care of reboot)

For some strange reason the scripts for umount (S03umountfs) were at the same level of S03reboot (or S03halt).

They are launched alphabetically so it results in launching reboot (or halt) scripts before cleanly umounting  the filesystems.

Hope it will help you.

P.S.
DO NOT CHANGE S scripts in K scripts.


dREI

---

### Post by dcstar on 2011-09-30
> **drei666 said:**
> Hi all,
I have Kubuntu 11.04 and I solved the problem just renaming 2 files:

1. rename /etc/rc0.d/S03halt in /etc/rc0.d/S99halt (takes care of shutdown)
2. rename /etc/rc6.d/S03reboot in /etc/rc6.d/S99reboot (takes care of reboot)

For some strange reason the scripts for umount (S03umountfs) were at the same level of S03reboot (or S03halt).

They are launched alphabetically so it results in launching reboot (or halt) scripts before cleanly umounting  the filesystems.

Hope it will help you.

P.S.
DO NOT CHANGE S scripts in K scripts.


dREI

Thank you very much for this. It solved my ongoing issue of ALL my non-root filesystems never being umounted cleanly before shutdown/reboot.

I believe that this may also solve this bug:

[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/616287](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/616287)

I will link a comment in the bug report to your post.

PS. On a fresh 10.04 install almost all the rc0/rc6 "S" scripts were numbered 01, so it seems that someone trying to minimise shutdown/reboot time has made a big mistake by trying to run everything in parallel when clearly that critical script should be run last.

---

### Post by myoldhouse on 2011-11-08
This unclean unmounting of partitions has been plaguing my Ubuntu desktop system since at least Ubuntu 10.04 (maybe even earlier). I have separate /, /home, and /usr/local partitions and all three would have orphaned inodes and need to recover their journals when booting or restarting. 

Under Ubuntu 11.10, shutdown was way too fast, maybe 3~4 seconds so I knew that files and programs and scripts were not getting a chance to shut down before a 'halt' or 'reboot' was executed.

So I looked in /etc/rc0.d and /etc/rc6.d for the S03halt and S03reboot symbolic links to the scripts in /etc/init.d (halt and reboot). On my system, the symbolic links to the scripts are all S01 prefixed instead of S03 but the logic works the same. I renamed /etc/rc0.d/S01halt to /etc/rc0.d/S99halt and /etc/rc6.d/S01reboot to /etc/rc6.d/S99reboot and now things unmount cleanly and shutdown in an orderly fashion.

And, no more orphaned inodes or journal recoveries on boot up or restart so my system starts much faster (~25 sec).

Thanks to drei666 for finding this simple and elegant fix to a really annoying problem. :D

---

### Post by mickyg on 2012-03-20
Hi, I know this is an old thread but I thought I would just add to it in case anyone stumbles across this having the same concerns... in answer to zigsterabg's post:

> My issue is that, by default, an Ubuntu system will not boot cleanly because the scripts to unmount the fs are never called because it is prefixed with an S. My understanding of SysV is that when you request a reboot it will run all the scripts prefixed with a K. As the scripts are prefixed with an S they are never called.

This is incorrect (at least for Debian based distros)... except from the Debian Policy Manual ([http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit]("http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit")):

> When init changes runlevel first the targets of the links whose names start with a K are executed, each with the single argument "stop", followed by the scripts prefixed with an S, each with the single argument "start".

...

The two runlevels 0 (halt) and 6 (reboot) are slightly different. In these runlevels, the links with an S prefix are still called after those with a K prefix, but they too are called with the single argument "stop".

So although changing them from "S" to "K" will still work, they are still called if they are "S".

As I said, I know this is an old post but if it helps, I like to think of the rc0.d and rc6.d scripts as "**S**tarting the shutdown/reboot process", and not as "**K**illing the system".

My two cents anyway :)

---

### Post by N4RPS on 2013-01-22
Hello!
I just thought I'd say that this helped me with my own umount issues. I was having the same thing happen with Lubuntu 12.10  - on a couple of different installations.
 
73 DE N4RPS
Rob

---

