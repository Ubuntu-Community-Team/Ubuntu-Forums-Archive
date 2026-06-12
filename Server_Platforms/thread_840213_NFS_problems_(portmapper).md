---
title: "NFS problems (portmapper?)"
date: 2008-06-25
forum: Server Platforms
---

### Post by slakkie on 2008-06-25
Hi all,

I've setup a NFS server, but I cannot mount my export..

sudo mount -t nfs slacker.euronet.nl:/mnt/samba/office-server/wndsrv002 /tmp/mnt
mount: slacker.euronet.nl:/mnt/samba/office-server/wndsrv002 failed, reason given by server: Permission denied

/etc/export
> 
/mnt/samba/office-server/wndsrv002 eniac(no_root_squash,ro,sync)


Showmount command on both server and client:


Export list for localhost: (server)
/mnt/samba/office-server/wndsrv002 eniac.euronet.nl

Export list for slacker.euronet.nl: (client)
/mnt/samba/office-server/wndsrv002 eniac.euronet.nl


When (re)starting the nfs-kernel-server:
> 
Jun 25 11:14:21 slacker kernel: [11655273.116507] RPC: failed to contact portmap (errno -5).
Jun 25 11:14:58 slacker kernel: [11655309.796894] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Jun 25 11:14:58 slacker kernel: [11655309.796921] NFSD: starting 90-second grace period


hosts.allow
> 
ALL: ALL
#portmap: 194.134.32.0/255.255.255.0
#rpc.mountd: 194.134.32.0/255.255.255.0


hosts.deny
> 
portmap: ALL


> 
ps -ef | grep portmap
daemon   16472     1  0 11:14 ?        00:00:00 /sbin/portmap

ps -ef | grep nfs
root     16506    11  0 11:14 ?        00:00:00 [nfsd4]
root     16507     1  0 11:14 ?        00:00:00 [nfsd]
root     16508     1  0 11:14 ?        00:00:00 [nfsd]
root     16509     1  0 11:14 ?        00:00:00 [nfsd]
root     16510     1  0 11:14 ?        00:00:00 [nfsd]
root     16511     1  0 11:14 ?        00:00:00 [nfsd]
root     16512     1  0 11:14 ?        00:00:00 [nfsd]
root     16513     1  0 11:14 ?        00:00:00 [nfsd]
root     16514     1  0 11:14 ?        00:00:00 [nfsd]

ps -ef | grep rpc
statd    12730     1  0 Jun24 ?        00:00:00 /sbin/rpc.statd
root     13252     1  0 Jun24 ?        00:00:00 /usr/sbin/rpc.idmapd
root     16504    11  0 11:14 ?        00:00:00 [rpciod/0]
root     16505    11  0 11:14 ?        00:00:00 [rpciod/1]
root     16518     1  0 11:14 ?        00:00:00 /usr/sbin/rpc.mountd


I haven't found anything on google mentioning the RPC -5 error (as seen in the messages.log). I'm somewhat puzzled by the problem, anyone that can provide any insight in my problem?

Ps. /etc/default/portmap has no entries, just comments...

Ps2. Both client and server are running on 7.04
Linux slacker.euronet.nl 2.6.20-16-server #2 SMP Sun Sep 23 19:57:25 UTC 2007 i686 GNU/Linux
Linux eniac.euronet.nl 2.6.20-15-386 #2 Sun Apr 15 07:34:00 UTC 2007 i686 GNU/Linux

Ps3. I don't get the portmap error in /var/log/messages when I remove one host (not displayed in my example) from /etc/exports

/mnt/samba/office-server/wndsrv002 nemo-p001(ro,sync) eniac(no_root_squash,ro,sync) -> RPC error in messsages file
/mnt/samba/office-server/wndsrv002 eniac(no_root_squash,ro,sync) -> No RPC error in messages file


In /var/log/syslog I get the following messages:

Jun 25 13:24:53 slacker mountd[17340]: authenticated mount request from eniac.euronet.nl:684 for /mnt/samba/office-server/wndsrv002 (/mnt/samba/office-server/wndsrv002)

---

### Post by roccivic on 2008-06-25
I followed these instructions and now got NFS working a treat:
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)
Hope this helps...

Rouslan

---

### Post by slakkie on 2008-06-25
> **roccivic said:**
> I followed these instructions and now got NFS working a treat:
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)
Hope this helps...

Rouslan

Thanks, but I already read that page (in order to verify wheter I did nothing wrong with my setup). I cannot find any differences..

---

### Post by lodp on 2008-06-25
I can't offer any expert advice, but things that come to mind, brainstorming:

1. i don't think you should post your actual URIs here

2. my /etc/exports (on my internal network) allows access on a per-IP basis. Entries look like this:
> 
/mnt 192.168.1.3(rw,root_squash,sync)

3. What firewall are you running? Does it even use hosts.allow / deny?

---

### Post by slakkie on 2008-06-26
> **lodp said:**
> I can't offer any expert advice, but things that come to mind, brainstorming:

1. i don't think you should post your actual URIs here

2. my /etc/exports (on my internal network) allows access on a per-IP basis. Entries look like this:


3. What firewall are you running? Does it even use hosts.allow / deny?

1. I do not believe in security through obscurity, I don't mind that you know what hostname I'm using. 

2. I should be able to hostnames or IP addresses in my export file, but I will give it a try based on IP addresses (haven't tried that).
2a. Tried the same based on the IP address of the host. It fails with the same error message: permission denied.

3. There is no firewall between the same machines, they are running in the same VLAN. Which rules out any ACL issue on the network level.

---

