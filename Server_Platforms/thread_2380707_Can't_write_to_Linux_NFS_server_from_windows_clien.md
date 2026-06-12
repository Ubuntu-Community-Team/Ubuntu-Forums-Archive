---
title: "Can't write to Linux NFS server from windows client"
date: 2017-12-20
forum: Server Platforms
---

### Post by lwheelden56 on 2017-12-20
I can't write to my nfs share, I've looked through other forums and still couldn't find anything.

my /etc/exports looks like this:

**/etc/NFSshare 192.168.0.1/200(rw,no_root_squash,sync)**

On the windows client, it shows a network share under 192.168.0.126, which is the server, but I can't write to it. 
I've already tried changing the ownership of the share directory (/etc/NFSshare) to the main user rather than root, but that didn't work.

---

### Post by darkod on 2017-12-21
For a start have you tried using * instead of 192.168.0.1/200 in the nfs export definition? That will allow all clients and at least you will see if it works like that. Later you can try to limit it to only specific clients.

Also, I haven't used NFS much and I'm not sure if 192.168.0.1/200 is the correct way to use it because it is not according to the CIDR notation. The number after the slash is usually in bits, not an IP in decimal format.

Anyway, try with * first and don't forget to restart the nfs service after changes to the exports file.

---

### Post by lwheelden56 on 2017-12-21
> **darkod said:**
> have you tried using * instead of 192.168.0.1/200 in the nfs export definition? 

The IP Address of the Windows Client is within that range, but I will try that.

---

### Post by lwheelden56 on 2017-12-21
Ok, now it looks like this:

[B]/etc/NFSshare *(rw,no_root_squash,sync)
[/B]

---

### Post by oldfred on 2017-12-21
for reference this is my exports:
```
fred@Asusz97:~$ cat /etc/exports
# /etc/exports: the access control list for filesystems which may be exported
#        to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/mnt/data   10.0.0.0/24(rw,no_root_squash,async)
/mnt/backup 10.0.0.0/24(rw,no_root_squash,async)

```
The example I followed was this:
 For Full Read Write Permissions allowing any computer from 192.168.1.1 through 192.168.1.255 
   

[LIST]
[*]/files 192.168.1.0/24(rw,no_root_squash,async)
[/LIST]

       HOWTO: NFS Server/Client if no windows 
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889) 
   [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
[http://mostlylinux.wordpress.com/network/nfshowto/](http://mostlylinux.wordpress.com/network/nfshowto/)

---

### Post by The Cog on 2017-12-21
192.168.0.1/200 is not valid. There is no way that the first 200 bits of this 32 bit number is the network number. I would suggest that maybe 192.168.0.0/24 might be better, covering IP address range 192.168.0.0-192.168.0.255.

Edit: beaten by oldfred.

---

### Post by lwheelden56 on 2017-12-21
I checked the Windows Client, but now, the server doesn't show up at all under Network in Windows Explorer. (I restarted the server, which should restart the nfs service) You can see such in the screenshot I have attached. The red circle indicates where the server should be. The computer to the left of it (whose name I have censored) is the windows client that I took the screenshot from.

---

### Post by darkod on 2017-12-21
I have no idea how NFS client works in windows. But as others have said, what you had in the export line was not valid. 192.168.0.1/200 does NOT mean 192.168.0.1-192.168.0.200 if that was your intention.

Your export should be fine now with the * in the definition. So now you have to work on the windows client and make sure it works OK.

By the way, does the server have a static IP? In your first post you mention 192.168.0.126 which looks like dhcp.

---

### Post by darkod on 2017-12-22
A quick search on google shows quite a few issues with windows nfs client. Even mentioning registry keys that need to be modified manually, permissions not working correctly, etc.

It just ocurred to me, why don't you simply use iscsi for windows clients? It is easy to set up iscsi target in ubuntu and windows has the iscsi initiator included since years ago and seems to me much more stable than the nfs client for production.

I would stick to nfs for linux clients and iscsi for windows, if it can work for you.

---

### Post by SeijiSensei on 2017-12-22
> **darkod said:**
> I would stick to nfs for linux clients and iscsi for windows, if it can work for you.

Or use Samba for Windows file sharing:  [https://help.ubuntu.com/lts/serverguide/samba.html](https://help.ubuntu.com/lts/serverguide/samba.html)

I run both NFS and Samba on a single server sharing the same files to Linux clients via NFS and Windows clients via Samba.

---

