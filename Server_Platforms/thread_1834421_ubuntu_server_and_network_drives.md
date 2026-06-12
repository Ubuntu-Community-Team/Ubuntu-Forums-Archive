---
title: "ubuntu server and network drives"
date: 2011-08-27
forum: Server Platforms
---

### Post by sangsterthegangster on 2011-08-27
hello. I have an old computer, so I decided to install ubuntu server 10.10 on it to use as a network drive for all my ubuntu computers, ipad, and android devices (I do not use windows). I installed samba on to it, and set up a share, but I can't get my ubuntu computers to auto mount to it using the following line in fstab.

```
//tjserver/networkshare /mnt/Network/server smbfs auto,username=jim,password=pass 0 0
```Just wondering if any one could help me. Also, I have heard that samba is not the best to use if you have no windows computers. Is there anything better out there?

---

### Post by drdos2006 on 2011-08-27
Set up a shared directory on a server and allow clients to connect to the shared server directory.
Assume the shared directory on the server is  “/media/sdb1/sdb1-server-shared”.
It is easier to set the server IP address to a fixed IP, the server can also be Ubuntu desktop version.
For Ubuntu 10.10 64bit.

From the NFSv4 server

Install the required packages...
sudo apt-get install nfs-kernel-server nfs-common
It may or may not be necessary to modify /etc/default/nfs-kernel-server with:
NEED_SVCGSSD=no # no is default
And the same here modify /etc/default/nfs-common with:
NEED_IDMAPD=yes
NEED_GSSD=no # no is default

To export ourserver directories to a local network 192.168.0.0/24
we add the following line to /etc/exports
/media/sdb1/sdb1-server-shared 192.168.0.0/24(rw,fsid=0,insecure,no_subtree_check,async) */ all on the one line of course */ or,
/media/sda3	192.168.0.0/24(async,crossmnt,insecure,no_subtree_check,rw,fsid=0)   */ or,
/media/sdb1 192.168.0.0/24(async,crossmnt,insecure,no_subtree_check,rw,fsid=1)*/ note the different fsid */

and restart the service with:
sudo /etc/init.d/nfs-kernel-server restart or reboot the server to allow NFS to change the permissions of the shared directory.

Change the permissions of /media/sdb1/sdb1-server-shared to allow read/write.

On the NFSv4 client which needs to access the server shared drive.
Install the required packages...
sudo apt-get install nfs-common
The client may need the same changes to /etc/default/nfs-common to connect to an NFSv4 server.
In /etc/default/nfs-common we set:
NEED_IDMAPD=yes
NEED_GSSD=no # no is default

From a terminal, create a new directory on the client with:
sudo mkdir /media/sdb1-server-shared
Mount the shared directory with:
sudo mount <server-IP-address>:/media/sdb1/sdb1-server-shared /media/sdb1-server-shared
######################################################################
If unable to mount try:
sudo mount -t nfs  <server-IP-address>:/media/sdb1-server-shared  /media/sdb1-server-shared
######################################################################

regards

---

### Post by sangsterthegangster on 2011-08-27
ok, that works thank everybody :P

---

### Post by kgatan on 2011-08-29
Not related to your problem but,
"smbfs" is outdated, use "cifs" instead.

---

