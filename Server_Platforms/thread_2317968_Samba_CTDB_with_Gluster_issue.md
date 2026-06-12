---
title: "Samba CTDB with Gluster issue"
date: 2016-03-21
forum: Server Platforms
---

### Post by ryan_3 on 2016-03-21
[FONT=verdana]Hey Team,[/FONT]
[FONT=verdana]Having an issue with Samba CTDB with Glusterfs. Receiving the following error in /var/log/ctdb/log.ctdb

[/FONT]
[FONT=verdana]2016/03/22 11:58:25.238975 [10343]: Unable to bind on ctdb socket '/var/lib/run/ctdb/ctdbd.socket' 
2016/03/22 11:58:25.239031 [10343]: Cannot continue. Exiting!

[/FONT]
[FONT=verdana]Here is the /etc/sysconfig/ctdb export[/FONT]
[FONT=verdana]CTDB_RECOVERY_LOCK=/cluster/clusterlock/lockfile
#CIFS ONLY[/FONT]
[FONT=verdana]CTDB_PUBLIC_ADDRESSES=/etc/ctdb/public_addresses 
CTDB_MANAGES_SAMBA=yes 
CTDB_MANAGES_WINBIND=yes
#CIFS ONLY[/FONT]
[FONT=verdana]CTDB_NODES=/etc/ctdb/nodes

[/FONT]
[FONT=verdana]Here is /etc/ctdb/nodes[/FONT]
[FONT=verdana]192.168.20.101 
192.168.20.102

[/FONT]
[FONT=verdana]and /etc/ctdb/public_addresses[/FONT]
[FONT=verdana]192.168.20.201/24 bond0 
192.168.20.202/24 bond0

[/FONT]
[FONT=verdana]Have been sure to add this into the smb.conf 
netbios name = cluster1 
clustering = yes idmap 
backend = tdb2 private 
dir = /cluster/clusterlock[/FONT]
[FONT=verdana]Can anyone see anything wrong here or advise what this error means. Checking around I can mainly see people fixing it due to wrong IPs and stuff, but in my case these are all correct. Any help would be great.[/FONT]
[FONT=verdana]Ta[/FONT]

---

### Post by Dave_Pryke on 2016-08-17
I know this is a few months old now, but I ran across this today, in pretty much the same situation, getting the logged error: [COLOR=#000000][FONT=verdana]***[FONT=courier new]Unable to bind on ctdb socket '/var/lib/run/ctdb/ctdbd.socket'[/FONT]***
[/FONT][/COLOR]*(Using Ubuntu 14.04.5, Samba 4.3.9-Ubuntu, CTDB 2.5.1)*

There ***iS*** an option that you can stick in **[FONT=courier new]/etc/default/ctdb[/FONT]** for the socket file: ```
CTDB_SOCKET=/var/run/ctdb/ctdbd.socket
```
But even after using that, I got the error: ***[FONT=courier new]Unable to open /var/lib/run/ctdb/.socket_lock[/FONT]***

I couldn't find any options that would allow me to change where that .socket_lock file was stored, so in the end, I just created the directory it was initially looking for: ```
mkdir -p /var/lib/run/ctdb
```
And that allowed me to continue on with my project. I just wanted to put that note here for anyone else that runs across this.

---

