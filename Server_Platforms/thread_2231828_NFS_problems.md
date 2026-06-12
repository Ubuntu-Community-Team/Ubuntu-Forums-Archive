---
title: "NFS problems"
date: 2014-06-28
forum: Server Platforms
---

### Post by Karl_May on 2014-06-28
Hi all

I am trying to set up an nfs server on say computer A running kubuntu 14.04.

my exports are

/home/usr/tmp *(rw,no_subtree_check,sync)

I am aware that now everyone who has the ip adresse of the host can mount /home/usr/tmp.

However, given what I have read in the NFS tutorial, hosts.allow/hosts.deny can put another barrier between the outside and the server. Thus my hosts.allow

ALL: 127.0.0.1

sshd: ALL

rpcbind mountd nfsd statd lockd rquotad : 127.0.0.1

portmap : 127.0.0.1

my hosts.deny

ALL: ALL

rpcbind mountd nfsd statd lockd rquotad : ALL

portmap: ALL


But I still can mount the file system from computer B, running kubuntu 14.04 as well, with "sudo mount.nfs4 server-ip:/home/usr/tmp /mnt/".

Thus, the nfs daemon is not evaluating the allow/deny settings (In fact I expect host.deny to work with ALL: ALL already, but thad didn't work either). Since the allow/deny setting are explicitly mentioned here [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

I currently don't know what I have done wrong.

Any idea

Cheers

Karl

---

### Post by Karl_May on 2014-06-28
sorry, can a moderator move this topic to the server platforms forum.

Thanks

Karl

---

### Post by coffeecat on 2014-06-28
> **Karl_May said:**
> sorry, can a moderator move this topic to the server platforms forum.


All done.

The best way to ask for a thread move is to use the "Report Post" button in your own post. A forum post might not be noticed by forum staff for some time, but a report can be dealt with quickly. It's OK to use the report button - we encourage its use for anything that requires forum staff attention, not just for reporting spam or problematic posts.

Good luck with getting a solution!

---

### Post by SeijiSensei on 2014-06-28
What do you see in /var/log/syslog when you try to mount the drive?

Frankly I'd never jump through all those hoops to limit access to the server.  I just use a CIDR address like 192.168.1.0/24 in /etc/exports.

---

### Post by gordintoronto on 2014-06-28
Did you mean host.deny or hosts.deny?

---

### Post by Karl_May on 2014-06-28
sorry, of course it is hosts.deny and hosts.allow. Have corrected the initial post

---

