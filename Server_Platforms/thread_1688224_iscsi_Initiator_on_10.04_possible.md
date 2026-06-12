---
title: "iscsi Initiator on 10.04 possible?"
date: 2011-02-15
forum: Server Platforms
---

### Post by skallen on 2011-02-15
Hi,

I have used open-iscsi for a couple of years on fedora and oracle linux, but since i use ubuntu for my desktop, web servers and mysql servers i thought i would be nice to do so on our new MySQL-server wich should be connected to our Qlogic SAN. 

The installation went well after figuring out how to put two network cards on the same network, wich seems to be the Qlogic way to do multipath. But i cannot make open-iscsi to log on automatically after rebbot. 

Is there something diffrent with open-iscsi on ubuntu?

Everything works if I logon and do:
iscsiadm -m node -l
multipath -v2

And then mount the volumes but if I try to put them in my fstab like:

/dev/MySQLdata/data		/var/lib/mysql/		ext4	_netdev	1 2
/dev/MySQLbackup/backup		/var/mysqlbackup	ext4	_netdev	1 2

I just won't work.

Hints anyone?

---

### Post by skallen on 2011-02-15
Of course it should be EqualLogic SAN and not Qlogic...

---

### Post by TheR on 2011-02-15
Did you try put every command into rc.local. Since Ubuntu is using upstart things don't start always as expected.

by
TheR

---

