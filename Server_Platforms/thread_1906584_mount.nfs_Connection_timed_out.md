---
title: "mount.nfs: Connection timed out"
date: 2012-01-09
forum: Server Platforms
---

### Post by Valpskott on 2012-01-09
Okay, so I just bought a ReadyNAS nv+ v2, installed an add-on so that I get root-access to it via ssh, and lo and behold, it was running something based on debian-squeeze (ARM).

On my previous NAS (ubuntu server) I mounted stuff with sshfs, but before retiring that NAS, I tried NFS and it was way faster and more reliable.

On the new NAS, I can mount via sshfs, but I'd really like to mount via NFS. I'm new to NFS, so I'd like some help.

What I've done so far.

Edited /etc/exports
```

/c/home/johan 10.10.1.190(rw,sync,no_subtree_check)
/c/home/johan 10.10.1.196(rw,sync,no_subtree_check)

```

Then I ran this
```
exportfs -r
```
Yielded no errors


Then I ran the following command
```
root@Amunet:/# /etc/init.d/portmap restart
Stopping portmap daemon....
Starting portmap daemon....
root@Amunet:/# /etc/init.d/nfs-common restart
Stopping NFS common utilities: idmapd statd.
Starting NFS common utilities: statd idmapd.
```


Then on my desktop machine (ubuntu 11.10) I ran
```
sudo mount 10.10.1.100:/c/home/johan /media/nellie
```
and
```
sudo mount -t nfs 10.10.1.100:/c/home/johan /media/nellie
```

which results in the error:
```
mount.nfs: Connection timed out
```

10.10.1.100 is the NAS... YES! "/c/home/johan" is the correct path to the directory I want to share. I guess the "c" is to make windows users comfortable so that they don't have to deal with the unix filesystem.


Another thing to mention is that, when I ordered this NAS, the shopping site listed it as having NFS support. But on Netgears site they have some pages that says it has NFS support and some that say it does not have NFS. The previous model had NFS. And clearly, the NFS software is there.

So, it might need some tinkering!

Anyone up for the challange?

---

### Post by Valpskott on 2012-01-09
More info:


```

root@Amunet:/# rpcinfo -p
program vers proto   port
100000    2   tcp    111  portmapper
100024    1   udp  45598  status
100024    1   tcp  36736  status
```

In another forum someone had...

```

100003 2 udp 2049 nfs
100003 3 udp 2049 nfs
100003 4 udp 2049 nfs
100003 2 tcp 2049 nfs
100003 3 tcp 2049 nfs
100003 4 tcp 2049 nfs
```

...which I am missing. What to do?

---

### Post by SeijiSensei on 2012-01-09
Usually the command to run the NFS server on Debian/Ubuntu is either "service nfs-kernel-server start" or "/etc/init.d/nfs-kernel-server start".

---

### Post by Valpskott on 2012-01-09
Dude, I remembered trying that before (a couple of software-reinstalments ago), and it didn't work, it said the server was already running.

For whatever reason, this time it said it started (tried it so I could hand you the same error-message). I tried mounting it... BAM!! it worked!

You sir, have made me one happy man! Thank you, thank you, thank you! :)

---

### Post by mdgmnas on 2012-01-09
Would suggest you do a
```

vi /etc/default/services

```

and set "NFS=1" (no quotes). This should mean that NFS is automatically started on each boot.

The information on NetGear.com should be being corrected.

ReadyNAS.com has a great community forum and a good comparison chart: [http://www.readynas.com/?cat=49](http://www.readynas.com/?cat=49)

---

### Post by mdgmnas on 2012-04-24
Some good news. NFS has been added as a feature in RAIDiator 5.3.5 (currently in beta: [http://www.readynas.com/forum/viewtopic.php?f=148&t=62728](http://www.readynas.com/forum/viewtopic.php?f=148&t=62728))

---

