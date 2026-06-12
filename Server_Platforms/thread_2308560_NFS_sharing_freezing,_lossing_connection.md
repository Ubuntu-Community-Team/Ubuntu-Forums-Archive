---
title: "NFS sharing freezing, lossing connection"
date: 2016-01-04
forum: Server Platforms
---

### Post by Berduchwal on 2016-01-04
I have a server which host a hard drive to which 3 other PC connect.
PC are connected over LAN. There are no security issues with users.
Sharing is done over NFS without authentication using fixed LAN IP addresses.

NFS is mounted using fstab entry:
```
192.0.0.0:/nfsexport/Common /media/Common nfs4 _netdev,auto 0 0

```

Server runs 15.10 Ubuntu and is not even reaching 5% memory or CPU usage.

However it is common for clients to have spreadsheet on which they work to freeze. It simply greys out for a minute or two. Sometimes forever.

```
cat /etc/exports
/nfsexport/Common/ 192.0.0.0(rw,nohide,no_subtree_check,sync)

```

Please suggest something I could do or try to fix this.

---

### Post by darkod on 2016-01-04
Did you actually use 192.0.0.0 as LAN IP for the server??? Or you hid the original IP?

I am asking because you never use (or almost never) the .0 address. It is the network addressing IP.

Have you tried changing the server LAN IP to 192.0.0.1 for example? Of course, this will result in changing it in all places where needed. But do not use .0 if that is really what you used...

PS. It slipped my mind, 192.0.0.0 is not even a private IP. So you probably used it as an example address. In such case you can disregard the above comment. But it does help if your server public IP does not end in .0 unless assigned like that from your provider. On the other hand if the server needs private IP it should be in the format 192.168.x.x.

---

### Post by Berduchwal on 2016-01-04
This was a fake IP address. I used it to cover up the real one. I am not sure it was worth it but I did it anyway.

Real IP addresses do not have 0 there they are more like 192.168.1.14 and so on.

---

### Post by darkod on 2016-01-04
I figured that out but after I posted... :)

Is it possible to test with 14.04 LTS server? You are using 15.10 which is non LTS release. I see non LTS as under constant development, trying things for the next LTS. I would never run a server with non LTS, not even for home. I can not guarantee it has an influence in this case, but maybe something in the nfs/networking in 15.10 is playing up on you...

Apart from that, since you say connectivity is good, it looks like you are doing everything right.

---

### Post by Berduchwal on 2016-01-04
I am currently using SSHFS as a backup. It works fine but also freezes from time time. NFS freezes to the point that only client reboot helps while SSHFS only freezes temporarily.

Sadly there was a bug in 14.04 which makes it very very hard to use sshfs with fstab. It got fixed in 15.10 that is why I upgraded. If I move back to 14.04 I might end up with no system which is to risky at the moment.

---

### Post by SeijiSensei on 2016-01-04
I mount SSHFS shares from /etc/rc.local rather than /etc/fstab with commands like:
```
sshfs -o uid=NNNN,gid=NNNN,allow_other,nonempty user@10.10.10.10:/path/to/remote/directory /path/to/mount/point
```
I have uid and gid parameters because I want to use the same user and group IDs on both machines since the directories are not owned by root.

---

### Post by Berduchwal on 2016-01-08
I change my Virgin Media Superhub router into modem mode and connected Cisco small business router to manage the traffic.

So far change was very good. No problems for the last 4 hours.

I noticed Cisco runs at 55% Memory capacity and CPU sometime jumps to 90%.

Is there anything I can do to lessen to load on the network?

---

