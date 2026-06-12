---
title: "NFS mount rw permission problem"
date: 2013-02-18
forum: Server Platforms
---

### Post by francesco_ljw on 2013-02-18
Hi Everyone:

I am mounting a directory from one linux server (which runs Centos) to my local ubuntu machine. A NFS server is running on the server machine and in /etc/exports I am setting the permission as (rw,sync). On my local computer I have the reading access to the directory content, however, I am not able to write to it. E.g., by touching a file "123.txt" in the mounted directory, I get the following response:

touch: cannot touch `123': Permission denied

I am totally a newbie and please kindly help me with some solution or guidance.

Thanks a lot in advance.

---

### Post by schragge on 2013-02-18
**On NFS server**
Ensure that nfsd re-reads /etc/exports after you've edited it (exportfs -ra)

**On client**
Check that NFS share is mounted rw (cat /proc/mounts).

**On both**
Check username mapping: telnet or ssh from the client into the NFS server and issue *id*. IIRC, the first created user gets by default (UID=501,GID=501) on Redhat-based systems, but (UID=1000,GID=1000) on Debian-based systems. So, there will be mismatch if you're using default values. One way to avoid it is to change the NFS options in /etc/exports to something like (rw,sync,all_squash,anonuid=501,anongid=501). Then all clients using the share will appear to be the local user with UID=501,GID=501.

---

### Post by francesco_ljw on 2013-02-19
Thanks a lot for the fast response, it works now and I can have RW permission to the remote directory !

However, there is still problem on the other server in the LAN and seems it DOES NOT allow NFS connection at all, although I setup [COLOR="red"]/etc/exports[/COLOR] on it and there is [COLOR="red"]portmap[/COLOR] and [COLOR="red"]nfsd[/COLOR] running on it ...

I tried to mount it from local desktop and after several minutes the machine responded as below:

[COLOR="Red"]mount.nfs: Connection timed out
[/COLOR]

I also tried from other computers and got the same results. 

Sorry for the troubles as I am totally a rookie linux user who just got the admin right to the server ... Is there any way I could follow to figure this out?

Thanks in advance.


> **schragge said:**
> **On NFS server**
Ensure that nfsd re-reads /etc/exports after you've edited it (exportfs -ra)

**On client**
Check that NFS share is mounted rw (cat /proc/mounts).

**On both**
Check username mapping: telnet or ssh from the client into the NFS server and issue *id*. IIRC, the first created user gets by default (UID=501,GID=501) on Redhat-based systems, but (UID=1000,GID=1000) on Debian-based systems. So, there will be mismatch if you're using default values. One way to avoid it is to change the NFS options in /etc/exports to something like (rw,sync,all_squash,anonuid=501,anongid=501). Then all clients using the share will appear to be the local user with UID=501,GID=501.

---

### Post by schragge on 2013-02-20
See the links:

[LIST]
[*][Linux NFS-HOWTO]("http://tldp.org/HOWTO/NFS-HOWTO/troubleshooting.html")
[*][NFS Gotchas]("http://www.troubleshooters.com/linux/nfs.htm#_Gotchas")
[*][Troubleshooting NFS]("http://www.bga.org/%7Elessem/psyc5112/usail/network/nfs/tips.html")
[*][Dan's tech tidbits: NFS troubleshooting]("http://stromberg.dnsalias.org/~dstromberg/NFS-troubleshooting-2.html")
[*][AIX Networks and communication management: NFS toubleshooting](http://publib.boulder.ibm.com/infocenter/pseries/v5r3/topic/com.ibm.aix.commadmn/doc/commadmndita/nfs_troublesh.htm)
[*][Solaris System Administration Guide: NFS Troubleshooting Procedures](http://docs.oracle.com/cd/E19455-01/806-0916/6ja8539fs)
[*][NFSv4 general troubleshooting recommendations]("http://wiki.linux-nfs.org/wiki/index.php/General_troubleshooting_recommendations")
[/LIST]

---

