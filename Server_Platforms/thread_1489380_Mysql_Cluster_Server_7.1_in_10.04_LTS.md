---
title: "Mysql Cluster Server 7.1 in 10.04 LTS"
date: 2010-05-21
forum: Server Platforms
---

### Post by Wasca on 2010-05-21
Hi Guys

With the new realease of Ubuntu 10.04 LTS, I was wondering if there was going to be a package for installing Mysql Cluster Server 7.1

If not does anyone know of a good walkthrough for compiling and installing it in Ubuntu 10.04 LTS?

Thanks

---

### Post by don_eddodo on 2010-05-26
looking for the same thing, I found these bugs:
[https://bugs.launchpad.net/ubuntu/+source/mysql-cluster-7.0/+bug/576528](https://bugs.launchpad.net/ubuntu/+source/mysql-cluster-7.0/+bug/576528)
[https://bugs.launchpad.net/ubuntu/+source/mysql-cluster-7.0/+bug/579732](https://bugs.launchpad.net/ubuntu/+source/mysql-cluster-7.0/+bug/579732)

Both are unnasigned... which seems strange since mysql shold be considered to be an important application for Ubuntu. Can't do much but wait.

Fred

---

### Post by thelner on 2010-05-27
The package mysql-cluster-server (in universe) installs mysqld Version 5.1.39-ndb-7.0.9-1ubuntu7. Unfortunately there is a bug in its packaging ([https://bugs.launchpad.net/ubuntu/+source/mysql-cluster-7.0/+bug/579732](https://bugs.launchpad.net/ubuntu/+source/mysql-cluster-7.0/+bug/579732)) making it a bit of a pain to install. It does work after a bit of post install database "surgery", please see: [https://bugs.launchpad.net/ubuntu/+source/mysql-cluster-7.0/+bug/579732/comments/5](https://bugs.launchpad.net/ubuntu/+source/mysql-cluster-7.0/+bug/579732/comments/5).

I am in the early stages of testing a cluster created by loosely following this guide:
[http://bieg.wordpress.com/2008/08/03/mysql-clustering-ubuntu/](http://bieg.wordpress.com/2008/08/03/mysql-clustering-ubuntu/)
Note: You will need to install "mysql-cluster-server" and not "mysql-server" as this guide states.

If you still want to compile from source this looks like a good guide:
[http://www.ctrip.ufl.edu/mysql-cluster-in-debian-lenny-howto](http://www.ctrip.ufl.edu/mysql-cluster-in-debian-lenny-howto)

---

### Post by don_eddodo on 2010-05-28
Thanks!

I am pretty novice though so I think I'll wait for the bug to be fixed.

Fred

---

### Post by don_eddodo on 2010-06-04
still no update or fix anyone?

Fredrik

---

### Post by thelner on 2010-06-10
There has been no visible activity on bug #579732 since my last post on May 26. It is still unassigned and has a status of "new". I don't know why it seems to be such a low priority, perhaps because mysql-cluster-server is in the universe repository.

The testing on my set up (using the workarounds I previously detailed to get it built) has been going well. But there is no way that I am willing to make it "production" until something happens w/ this bug.

---

### Post by don_eddodo on 2010-06-23
exactly we feel the same...

Fredrik

---

### Post by nicolasdiogo on 2010-11-06
Hi,

has there been any changes on mysql cluster for 10.04 LTS installation?

thanks,

Nicolas

[www.brainpowered.net](www.brainpowered.net)

---

### Post by severalniens on 2011-01-07
Hi,

Currently, what I can see it is not possible to install MySQL Cluster 7.1 in Ubuntu, and 7.0.9b is really old and I don't really recommend that version anyway.

However, if you want to install latest MySQL Cluster 7.1  (and complete with init.d scripts), then you can go to [http://www.severalnines.com/config]("http://www.severalnines.com/config") and generate a configuration for your cluster, complete with scripts to install and manage it.

When you get the config package you do:

tar xvfz mysqlcluster-71.tar.gz
cd mysqlcluster-71/cluster/scripts/install
./download-binary.sh
(answer yes if you want to install the binary every where)
./bootstrap.sh     ##setup the datadirectories, create mysql user etc
cd ..
./start-cluster --initial

and you are up and running in 10 minutes (DL time basically)  (you should have shared ssh keys setup for the root account).

This also works in EC2


BR
johan

---

