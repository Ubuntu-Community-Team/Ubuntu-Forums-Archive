---
title: "NFS4 sharing root filesystem instead of mounted drive"
date: 2013-04-02
forum: Server Platforms
---

### Post by Andyrue on 2013-04-02
This is what I've done

mkdir /exports
mkdir /exports/back

This 12TB drive is what I want to share.
/dev/sdb1                   12T  9.2T  2.0T  83% /media/back

mount --bind /media/back /exports/back

#/etc/exports
/exports    10.111.106.4(rw,fsid=0,insecure,no_subtree_check,sync)
/exports/back 10.111.106.4(rw,fsid=0,insecure,no_subtree_check,sync)

When I mount on the client with

mount -t nfs4 10.111.106.12:/back /mnt/back

it is successful, but a df shows that it's only a 71GB drive (which is my local filesystem)
10.111.106.12:/back    71G   16G   52G  24% /mnt/back
I expect it to be a 12TB drive.

I'm only having this problem because I upgraded my backup server to 'precise' and now I can't mount nfs3 from my 10.04 client, and nfs2 won't cut it for my file sizes.  NFS4 mounts, but it's just not working properly.  Help!

---

### Post by ranger12 on 2013-04-03
Hi, I have one question. What machine is the ip 10.111.106.4 to? Is it your server or a specific workstation? I just want to get some clarification on which ip address belongs to which machine before I stick my foot in my mouth.

---

### Post by Andyrue on 2013-04-03
> **ranger12 said:**
> Hi, I have one question. What machine is the ip 10.111.106.4 to? Is it your server or a specific workstation? I just want to get some clarification on which ip address belongs to which machine before I stick my foot in my mouth.

10.111.106.4 is my File Server (nfs client in this case)
10.111.106.12 is my Backup Server (nfs server in this case)

---

### Post by Andyrue on 2013-04-03
I'm going to mark this as solved...I honestly think something had gotten corrupted when I upgraded to 12.04.  The NFS problem wasn't my first clue, and my last clue was when I rebooted and couldn't even get the system to load.  I figured I'd just do a quick reinstall and now everything is working as intended again.

---

