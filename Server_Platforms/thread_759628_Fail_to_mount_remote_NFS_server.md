---
title: "Fail to mount remote NFS server"
date: 2008-04-19
forum: Server Platforms
---

### Post by satimis on 2008-04-19
Hi folks,


Server A
Ubuntu server 6.06.4 amd64
hostname=lampserver
IP add - 192.168.0.52

Server B
Ubuntu server 7.04 amd64
hostname=mail.satimis.com
IP add - 192.168.0.1


They are connected to the same router.  

Server A

$ sudo /etc/init.d/nfs-kernel-server start```

 * Exporting directories for NFS kernel daemon...                        [ ok ] 
 * Starting rpc nfsd...                                                  [ ok ] 
 * Starting rpc mountd...                                                [ ok ] 
```


Server B
$ sudo /etc/init.d/nfs-kernel-server start```

 * Exporting directories for NFS kernel daemon...                               exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "*:/ubuntu".
  Assuming default behaviour ('subtree_check').
  NOTE: this default will change with nfs-utils version 1.1.0
exportfs: /etc/exports [2]: Neither 'subtree_check' or 'no_subtree_check' specified for export "*:/home".
  Assuming default behaviour ('subtree_check').
  NOTE: this default will change with nfs-utils version 1.1.0
                                                                         [ OK ]
 * Starting NFS kernel daemon                                            [ OK ] 

```
Here it seems having problem.  Please advise where to check and how to fix the problem


Server A

$ sudo mount mail.satimis.com:/ubuntu /mnt```

mount to NFS server 'mail.satimis.com' failed: server is down.

```


B.R.
satimis

---

### Post by Deathrend on 2008-04-19
Try mounting it using the IP address instead of the host name.

It looks like your DNS isn't resoving the host.  I know with mine, I'm using two windows DNS hosts, so they won't resolve anything that's not a meber of Active Directory, unless I put in the records by hand.

---

### Post by satimis on 2008-04-19
> **Deathrend said:**
> Try mounting it using the IP address instead of the host name.
Tried already

$ sudo mount 192.168.0.10:/ubuntu /mnt

Only hanging there


B.R.
satimis

---

### Post by Deathrend on 2008-04-19
D'oh, I don't deal with Linux to linux mounts that often sadly -_-

You should see thecomplicated mounts I use though >.>

sudo mount -t cifs //192.168.1.15/storage /mnt/srv1 -o iocarset=utf8,file_mode=0777,dir_mode=0777,username=Administrator@homelan.loc,password=password

Most of my linux servers are running on fairly small SCSI's, then all of my storage resides on a server running 2003 Enterprise (yeah yeah yeah..) to access it, I use that.

---

### Post by satimis on 2008-04-19
> **Deathrend said:**
> D'oh, I don't deal with Linux to linux mounts that often sadly -_-

You should see thecomplicated mounts I use though >.>

sudo mount -t cifs //192.168.1.15/storage /mnt/srv1 -o iocarset=utf8,file_mode=0777,dir_mode=0777,username=Administrator@homelan.loc,password=password

Most of my linux servers are running on fairly small SCSI's, then all of my storage resides on a server running 2003 Enterprise (yeah yeah yeah..) to access it, I use that.
Actually I can connect them with ssh.


Just follow;
Ubuntu Server Guide
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/index.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/index.html)

building Server A.  


Coming to "NFS Client Configuration" 
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/network-file-system.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/network-file-system.html)

I mount Server B according to the manual.



B.R.
satimis

---

### Post by netztier on 2008-04-20
Can you show us the **/etc/exports** file of the server you are trying to mount from?

regards

Marc

---

### Post by satimis on 2008-04-20
> **netztier said:**
> Can you show us the **/etc/exports** file of the server you are trying to mount from?

regards

Marc
Hi Marc,


Server B

$ cat /etc/exports ```

# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
/ubuntu  *(ro,sync,no_root_squash)
/home    *(rw,sync,no_root_squash)

```
Thanks


B.R.
satimis

---

