---
title: "Unable to edit files on NFSv4 Shares"
date: 2009-04-16
forum: Server Platforms
---

### Post by Dragonmantank on 2009-04-16
I followed the directions [here]("https://help.ubuntu.com/community/NFSv4Howto") to set up NFSv4 without Kerberos on an Ubuntu 8.04.2 server and exported the folders and can mount them on an external box running Ubuntu 8.04.2-server. However, the external box cannot do anything but read from the exported folders, I get permission denied (even as root) whenever I try to modify files or create new ones.

NFS SERVER:
/etc/exports
```
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

/exports           192.168.60.10(rw,fsid=0,insecure,no_subtree_check,async)
/exports/stable    192.168.60.10(rw,nohide,insecure,no_subtree_check,async)
/exports/trunk     192.168.60.10(rw,nohide,insecure,no_subtree_check,async)
/exports/unstable  192.168.60.10(rw,nohide,insecure,no_subtree_check,async)
/exports/unstable2 192.168.60.10(rw,nohide,insecure,no_subtree_check,async)
/exports/unstable3 192.168.60.10(rw,nohide,insecure,no_subtree_check,async)
```

and I used the samples for the other files that the HowTo listed.

Any ideas?

---

### Post by idivert on 2009-05-04
I am having the same problem, did you have any luck resolving this?

---

### Post by MilkBoy on 2009-10-16
Just a "me too" post. This debug info from (client) doesn't really tell me anything..

Oct 16 22:24:02 mythbackend kernel: [626089.350209] NFS: permission(0:18/2), mask=0x1, res=0
Oct 16 22:24:02 mythbackend kernel: [626089.350218] NFS: nfs_lookup_revalidate(/) is valid
Oct 16 22:24:02 mythbackend kernel: [626089.355172] NFS: permission(0:18/2), mask=0x1, res=0
Oct 16 22:24:02 mythbackend kernel: [626089.355180] NFS: permission(0:18/2), mask=0x1, res=0
Oct 16 22:24:02 mythbackend kernel: [626089.355188] NFS: permission(0:18/2), mask=0x3, res=0
Oct 16 22:24:02 mythbackend kernel: [626089.355192] NFS: create(0:18/2), test
Oct 16 22:24:02 mythbackend kernel: [626089.355221] encode_compound: tag=
Oct 16 22:24:02 mythbackend kernel: [626089.355598] NFS: permission(0:18/2), mask=0x1, res=0
Oct 16 22:24:02 mythbackend kernel: [626089.355605] NFS: atomic_lookup(0:18/2), test
Oct 16 22:24:02 mythbackend kernel: [626089.355609] NFS: lookup(/test)
Oct 16 22:24:02 mythbackend kernel: [626089.355613] NFS call  lookup test
Oct 16 22:24:02 mythbackend kernel: [626089.355616] NFS call  lookupfh test
Oct 16 22:24:02 mythbackend kernel: [626089.355623] encode_compound: tag=
Oct 16 22:24:02 mythbackend kernel: [626089.355650] NFS: dentry_delete(/test, 18)
Oct 16 22:24:02 mythbackend kernel: [626089.355809] NFS reply lookupfh: -2
Oct 16 22:24:02 mythbackend kernel: [626089.355812] NFS reply lookup: -2
Oct 16 22:24:02 mythbackend kernel: [626089.355818] NFS: dentry_delete(/test, 0)

---

### Post by karlson on 2009-10-16
> **Dragonmantank said:**
> I followed the directions [here]("https://help.ubuntu.com/community/NFSv4Howto") to set up NFSv4 without Kerberos on an Ubuntu 8.04.2 server and exported the folders and can mount them on an external box running Ubuntu 8.04.2-server. However, the external box cannot do anything but read from the exported folders, I get permission denied (even as root) whenever I try to modify files or create new ones.

NFS SERVER:
/etc/exports
```
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

/exports           192.168.60.10(rw,fsid=0,insecure,no_subtree_check,async)
/exports/stable    192.168.60.10(rw,nohide,insecure,no_subtree_check,async)
/exports/trunk     192.168.60.10(rw,nohide,insecure,no_subtree_check,async)
/exports/unstable  192.168.60.10(rw,nohide,insecure,no_subtree_check,async)
/exports/unstable2 192.168.60.10(rw,nohide,insecure,no_subtree_check,async)
/exports/unstable3 192.168.60.10(rw,nohide,insecure,no_subtree_check,async)
```

and I used the samples for the other files that the HowTo listed.

Any ideas?

Can you post the client's /etc/fstab?  Also is someone mounting /exports?

---

### Post by kevarh on 2009-11-02
Same issue here, anyone solve this?

---

### Post by cariboo on 2009-11-03
The way you have your exports setup you can only access them from one computer, 192.168.60.10

I use the following:

```
/media/movies	192.168.1.0/24(rw,sync,no_subtree_check)
```

I then mount the shares manually as needed using this command:

```
willy:/media/movies /media/movies
```

I have the server name aliased to an ip address in /etc/hosts

---

### Post by kevarh on 2009-11-03
I have the same problem in that after some period of time, writes will always be met with a permission denied error. Reads still work correctly, and writing to a folder chmod 777 still works. ls shows the appropriate users and groups, but writes are still not allowed.

---

### Post by steve_c on 2010-01-22
Sorry to bump an old thread but I'm having this issue as well. Like the OP, I followed the instructions [here]("https://help.ubuntu.com/community/NFSv4Howto"). I was able to mount and am able to read successfully. However the UID/GID from the client machine is a jumble of numbers even though the user/group IDs on both machines match. Even root cannot write the mounted directory.
e.g.
```
user@client:/mnt/storage$ ls -l
total 16
drwx------ 2 4294967294 4294967294 16384 2010-01-21 22:57 lost+found
user@client:~$ sudo mkdir /mnt/storage/folder
mkdir: cannot create directory `/mnt/storage/folder': Permission denied
```
Both my /etc/exports on the server and my /etc/fstab on the client are as in the instructions (including the rw option). Am I overlooking something simple? Has anyone gotten NFSv4 working and writable without kerberos on Ubuntu?

Thanks.

---

### Post by Xianath on 2010-01-22
I remember running into this issue when I was setting up NFSv4 about a year ago and having started from this very howto. Do you have rpc.idmapd running on both the client and server?

Regards,
Peter

---

### Post by steve_c on 2010-01-24
Finally got it working. Not *entirely* sure what I did.
I set this in /etc/default/nfs-common on the client (I'd already set it this way on the server):
```
NEED_IDMAPD=yes
NEED_GSSD=no
```

Upon rebooting both the client and the server they could now get the right UID/GID on the files.

To make it read/writable, on the server I did the following:
```
$ chown -R root:users /exports/storage
$ chmod 777 /exports/storage
```
And on the client I changed my /etc/fstab to include the rw option (not sure if this was necessary):
```
# Soma storage array (NFSv4)
soma:/storage   /mnt/storage    nfs4    rw,_netdev,auto 0       0

```

Everything *seems* to be working now. Is there any way for me to check that this is really using nfs4 and not nfs3? Or does the nfs4 switch in the client's fstab guarantee that?

---

### Post by Xianath on 2010-01-25
The mount command should give you a list of all mounted locations, I guess it would tell you if it's NFSv4 or not. Other than that, sniffing the network is always an option :)

Cheers,
Peter

---

