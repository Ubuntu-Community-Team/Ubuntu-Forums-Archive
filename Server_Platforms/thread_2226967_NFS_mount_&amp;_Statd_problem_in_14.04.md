---
title: "NFS mount &amp; Statd problem in 14.04"
date: 2014-05-29
forum: Server Platforms
---

### Post by mattlach on 2014-05-29
Hey all,

Fresh install of Ubuntu Server edition 14.04 here.   Barely touched, except for network config (editing /etc/network/interfaces) and doing a full update using apt-get.

I got stuck with an NFS mount problem.

I installed rpcbind and nfs-common

When I try to mount a remote NFS share I get the following:

```
mount.nfs: rpc.statd is not running but is required for remote locking.
mount.nfs: Either use '-o nolock' to keep locks local, or start statd.
mount.nfs: an incorrect mount option was specified
```

I know statd is a part of nfs-common, and I thought the service was already mounting, but just to check I did "service statd start" and got the following result:

```
start: Job is already running: statd
```

So something is clearly wrong.

a search of the logs for anything statd results in the following:

```
$ grep statd /var/log/*
grep: /var/log/apt: Is a directory
/var/log/auth.log:May 29 20:54:58 ubuntu-server useradd[1939]: new user: name=statd, UID=105, GID=65534, home=/var/lib/nfs, shell=/bin/false
/var/log/auth.log:May 29 20:54:58 ubuntu-server usermod[1944]: change user 'statd' password
/var/log/auth.log:May 29 20:54:58 ubuntu-server chage[1949]: changed password expiry for statd
/var/log/auth.log:May 29 21:00:53 ubuntu-server dbus[364]: [system] Rejected send message, 1 matched rules; type="method_call", sender=":1.5" (uid=1000 pid=1209 comm="start statd ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init ")
/var/log/auth.log:May 29 21:01:07 ubuntu-server sudo:     matt : TTY=pts/3 ; PWD=/home/matt ; USER=root ; COMMAND=/usr/sbin/service statd start
/var/log/auth.log:May 29 21:05:35 ubuntu-server sudo:     matt : TTY=pts/3 ; PWD=/home/matt ; USER=root ; COMMAND=/bin/grep statd /var/log/alternatives.log /var/log/apt /var/log/auth.log /var/log/boot.log /var/log/bootstrap.log /var/log/btmp /var/log/dist-upgrade /var/log/dmesg /var/log/dmesg.0 /var/log/dmesg.1.gz /var/log/dmesg.2.gz /var/log/dmesg.3.gz /var/log/dpkg.log /var/log/faillog /var/log/fsck /var/log/installer /var/log/kern.log /var/log/landscape /var/log/lastlog /var/log/syslog /var/log/udev /var/log/unattended-upgrades /var/log/upstart /var/log/wtmp
/var/log/boot.log: * Starting Block the mounting event for NFS filesytems[ OK ] statd is running
/var/log/boot.log: * Stopping Block the mounting event for NFS filesytems[ OK ] statd is running
grep: /var/log/dist-upgrade: Is a directory
/var/log/dmesg:[    6.537848] init: statd-mounting (/mnt/FreeNAS) main process (281) killed by TERM signal
grep: /var/log/fsck: Is a directory
grep: /var/log/installer: Is a directory
grep: /var/log/landscape: Is a directory
/var/log/syslog:May 29 20:54:58 ubuntu-server rpc.statd[1992]: Version 1.2.8 starting
/var/log/syslog:May 29 20:54:58 ubuntu-server rpc.statd[1992]: Flags: TI-RPC 
/var/log/syslog:May 29 20:54:58 ubuntu-server rpc.statd[1992]: Failed to read /var/lib/nfs/state: Success
/var/log/syslog:May 29 20:54:58 ubuntu-server rpc.statd[1992]: Initializing NSM state
/var/log/syslog:May 29 20:56:54 ubuntu-server rpc.statd[2157]: Version 1.2.8 starting
/var/log/syslog:May 29 20:56:54 ubuntu-server rpc.statd[2157]: Flags: TI-RPC 
/var/log/syslog:May 29 20:58:05 ubuntu-server statd-pre-start: virtual-filesystems started
/var/log/syslog:May 29 20:58:05 ubuntu-server rpc.statd[868]: Version 1.2.8 starting
/var/log/syslog:May 29 20:58:05 ubuntu-server rpc.statd[868]: Flags: TI-RPC 
/var/log/syslog:May 29 20:58:05 ubuntu-server rpc.statd[911]: Version 1.2.8 starting
/var/log/syslog:May 29 20:58:05 ubuntu-server rpc.statd[911]: Flags: TI-RPC 
/var/log/syslog:May 29 20:58:33 ubuntu-server rpc.statd[1202]: Version 1.2.8 starting
/var/log/syslog:May 29 20:58:33 ubuntu-server rpc.statd[1202]: Flags: TI-RPC 
/var/log/syslog:May 29 21:01:15 ubuntu-server rpc.statd[1226]: Version 1.2.8 starting
/var/log/syslog:May 29 21:01:15 ubuntu-server rpc.statd[1226]: Flags: TI-RPC 
grep: /var/log/unattended-upgrades: Is a directory
grep: /var/log/upstart: Is a directory

```

I really would appreciate any assistance or theories regarding what might be going on here.

Thanks,
Matt

---

### Post by steeldriver on 2014-05-29
Firewall blocking the rpcbind port (111) maybe?

---

### Post by mattlach on 2014-05-29
> **steeldriver said:**
> Firewall blocking the rpcbind port (111) maybe?

You got it.  I had a typo in /etc/hosts.allow

I am way too tired. Making more mistakes than progress...   Should call it quits for the night.

---

