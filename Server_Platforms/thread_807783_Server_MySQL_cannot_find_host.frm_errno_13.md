---
title: "Server: MySQL cannot find host.frm errno 13"
date: 2008-05-26
forum: Server Platforms
---

### Post by infecticide on 2008-05-26
Hello,

I am in the process of moving a bunch of databases from one machine to another.  No big deal, or so I thought.

My issue seems to lie with the mysql directory where the permissions tables and such reside.

Here is the error I get:

> 
$ sudo /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
080526  3:05:01 [Warning] Can't create test file /var/lib/mysql/kubeunto.lower-test
080526  3:05:01 [Warning] Can't create test file /var/lib/mysql/kubeunto.lower-test
080526  3:05:01 [ERROR] /usr/sbin/mysqld: Can't find file: './mysql/host.frm' (errno: 13)
080526  3:05:01 [ERROR] /usr/sbin/mysqld: Can't find file: './mysql/host.frm' (errno: 13)
080526  3:05:01 [ERROR] Fatal error: Can't open and lock privilege tables: Can't find file: './mysql/host.frm' (errno: 13)


I can assure you the permissions are more than adequate at this point.

I also get this message in the system logs:
> 
May 26 03:05:01 kubeunto kernel: [  654.411957] audit(1211792701.299:18): type=1503 operation="inode_create" requested_mask="w::" denied_mask="w::" name="/mnt/web/mysql/kubeunto.lower-test" pid=5060 profile="/usr/sbin/mysqld" namespace="default"
May 26 03:05:01 kubeunto kernel: [  654.412723] audit(1211792701.299:19): type=1503 operation="inode_create" requested_mask="w::" denied_mask="w::" name="/mnt/web/mysql/kubeunto.lower-test" pid=5060 profile="/usr/sbin/mysqld" namespace="default"
May 26 03:05:01 kubeunto kernel: [  654.420070] audit(1211792701.309:20): type=1503 operation="inode_permission" requested_mask="r::" denied_mask="r::" name="/mnt/web/mysql/mysql/host.frm" pid=5060 profile="/usr/sbin/mysqld" namespace="default"
May 26 03:05:01 kubeunto kernel: [  654.420903] audit(1211792701.309:21): type=1503 operation="inode_permission" requested_mask="r::" denied_mask="r::" name="/mnt/web/mysql/mysql/host.frm" pid=5060 profile="/usr/sbin/mysqld" namespace="default"


I assume apparmor or some other security layer has something to do with this.  How to I fix this?

---

### Post by infecticide on 2008-05-26
On my own insight, I found the solution here: [http://ubuntuforums.org/showthread.php?t=804126&highlight=apparmor+mysql](http://ubuntuforums.org/showthread.php?t=804126&highlight=apparmor+mysql)  

AppArmor was indeed the culprit.

---

### Post by hyper_ch on 2008-05-26
you shouldn't copy the binaries themselves... well, you can but also make a mysql dump first to be sure.

---

