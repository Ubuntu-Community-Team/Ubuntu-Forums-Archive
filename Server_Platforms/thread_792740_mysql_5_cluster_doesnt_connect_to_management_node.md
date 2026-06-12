---
title: "mysql 5 cluster doesnt connect to management node"
date: 2008-05-13
forum: Server Platforms
---

### Post by matthew malkin on 2008-05-13
i have set up a mysql cluster as described in the documentation for mysql-server-5.0

i have the management node on 1 machine, and then 2 more machines which both have mysqld and ndbd set up on them
as far as i can tell, the management server is working fine, and the ndbd portion of the cluster is also working fine, output from:



 ```
   ndb_mgm>show
    Cluster Configuration
    ---------------------
    [ndbd(NDB)] 2 node(s)
    id=2 @*.*.*.230 (Version: 5.0.51, starting, Nodegroup: 0)
    id=3 @*.*.*.231 (Version: 5.0.51, starting, Nodegroup: 0)

    [ndb_mgmd(MGM)] 1 node(s)
    id=1 (Version: 5.0.32)

    [mysqld(API)] 2 node(s)
    id=4 (not connected, accepting connect from any host)
    id=5 (not connected, accepting connect from any host)

```


my problem is whatever i seem to do, the mysqld nodes will not connect to the management node

i have been careful to start the system in the order described in the manual,
both the ndbd/mysqld machines were set up at the same time and are identical.
both the ndbd/mysqld machines run ubuntu server 8.04 and mysql 5.0.51
both the ndbd/mysqld machines are 64 bit xeon machines with the amd64 version of ubuntu
the management server is debian 4.1, and running mysql 5.0.32 it is a celeron with the x86 version of debian
the config file on both the ndbd/mysqld machines is /etc/mysql/my.cnf and it reads:



   ```

    [mysqld]
    ndbcluster
    ndb-connectstring=management.domain.tld
    [mysql_cluster]
    ndb-connectstring=management.domain.tld

```


the config file on the management server is /etc/mysql/ndb_mgmd.cnf and it reads:

```

    [ndbd default]
    NoOfReplicas=2
    DataMemory=80M
    IndexMemory=18M

    [tcp default]

    [ndb_mgmd]
    hostname=management.domain.tld
    datadir=/var/lib/mysql-cluster

    [ndbd]
    hostname=db1.domain.tld
    datadir=/usr/local/mysql/data

    [ndbd]
    hostname=db2.domain.tld
    datadir=/usr/local/mysql/data

    [mysqld]
    [mysqld]


```

to check if i could see the management server from the connecting hosts i did a telnet to port 1186, and then get version command, which returned the correct info

so if anyone has any ideas why the mysqld nodes don't connect i would much appreciate some pointers.

Thanks

p.s.

i have tried to give as much detail as possible, also i can't find any logs, at least no logs with anything written in them, plenty of completely empty ones.
if more details are required please let me know.

---

### Post by CheShA on 2009-10-27
Did you solve this? I'm having the same problem.

---

### Post by CheShA on 2009-10-28
It was simple enough, I had to open port 1186 across all servers in the cluster.

---

### Post by matthew malkin on 2009-10-29
Hi yea. for future reference i solved my issues also. different problem to you though it seems. i replaced my domain and host names with ip addresses and this solved the problem. not sure why it was a problem as the hostnames resolved to the same ip's that i used in the config, and the machines were able to resolve them, but there we go. hopefully that'll help someone in the future.

---

### Post by igorm80 on 2009-12-04
Hey guys,

-I am having the same issue. No matter what I do, the mysql does not connect to the management node. All services are run on a single machine for now. I run tcpdump on the management port - I dont see any connection attempts from the mysqld at all..

Can someone please help me spot the issue?

Thanks!

Here are the configs:

//my.cnf
//----------------
[mysqld]
ndb-nodeid=51
ndbcluster
ndb-connectstring=192.168.30.101
port=3306
server-id=51
log-bin

//ndb_mgmd.cnf
//------------------
noofreplicas=2
DataMemory=80M
IndexMemory=18M

[MYSQLD DEFAULT]
[NDB_MGMD DEFAULT]
[TCP DEFAULT]

[ndbd]
hostname=192.168.30.191
id=1
DataMemory=512M

[ndbd]
hostname=192.168.30.192
id=2
DataMemory=512M

[ndb_mgmd]
id = 11
hostname=192.168.30.191

[ndb_mgmd]
id = 12
hostname=192.168.30.192

[mysqld]
id=51
hostname=192.168.30.191

[mysqld]
id=52
hostname=192.168.30.192

---

