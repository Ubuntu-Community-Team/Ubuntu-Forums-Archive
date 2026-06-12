---
title: "nfs madness"
date: 2007-01-09
forum: Server Platforms
---

### Post by enatiello on 2007-01-09
Howdy,
I have a few boxes running ubuntu linux server installed from the same CD.  Identical hardware.
Linux host4 2.6.15-26-server #1 SMP Thu Aug 3 04:09:15 UTC 2006 i686 GNU/Linux
Linux host3 2.6.15-26-server #1 SMP Thu Aug 3 04:09:15 UTC 2006 i686 GNU/Linux

I have a NAS device sharing a directory named /export

I have added a line similar to the following in /etc/fstab on both servers:
NAS:/export        /export         nfs     rw,nolock 0 0

On one of the boxes, the /export directory mounts properly, however there is no entry when I do "mount" from the terminal.  Also /etc/mtab doesn't show /export being mounted.  
I _can_ cd into /export and get to anything on the share.

On another box, the mount command never showed /export as being mounted and it never was.  I could cd into /export but it was clearly not mounted as the dir was empty.  After ssh was available, running mount -a would mount the nfs partition.

Local drives on both boxes mount without an issue.

I am looking for a few things:
. Is not seeing the /export share when running "mount" expected behavior?
. Where should I be looking explain the differences I am seeing in the two machines?
. wtf?

Thanks,
Ern

---

### Post by hal10000 on 2007-01-09
I found this link which might hekp you

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by enatiello on 2007-01-11
Thanks for the reply.  :)  It gave me something to check my setup against.

My nfs partitions work just fine, except that they are not mounted at boot time, however a "mount -a" mounts the partition.  This tells me that my nfs, fstab, hosts, permissions... are all setup correctly.


Installation:
I installed portmap and nfs-common on _one_ of the boxes.  It made no difference in behavior between the two boxes.  On both, after booting, from the terminal I can run "mount -a" and /export mounts just fine.  The partition is still not mounted during init.

Portmap Lockdown:
I am not using hosts.deny or hosts.allow, so we'll skip that part.

Hostnames:
My /etc/hosts file is all setup, as well as resolv.conf for DNS.

Mounts:
I can mount everything, except it is not mounting upon boot.  After the box is up and running, I can ssh into the box and run "mount -a" and it mounts.

The problem with this is I have services starting on the box that require things on my nfs /export at boot time.  There is currently a script we are running that mounts the partition, however as we roll out more boxes, this becomes a huge nightmare to manage let alone a troubleshooting nightmare for anyone who didn't engineer the box.


I could still use some help.

Thanks,
Ern

---

### Post by hal10000 on 2007-01-11
I'm not sure if i really understand your problem, but usually you don't need to mount /export on your nfs server box, you only need to mount the exported partitions (from nfs server box) on the clients that want to get coneected to the nfs servers.

So what do i get wrong here?

---

### Post by enatiello on 2007-01-11
I have a NAS device that is supplying the /export nfs

my clients are ubuntu boxes, that are not mounting this partition on boot.

---

### Post by hal10000 on 2007-01-11
Ok, i guess i've got it. Your server boxes receive their mounts from a nas (server) that's storage is provided over nfs (so your server boxes are clients to the nfs (nas).

But i'm sorry to have no idea why why it don't works at boot time.

---

### Post by enatiello on 2007-01-11
> **hal10000 said:**
> But i'm sorry to have no idea why why it don't works at boot time.

That's OK.  Me either.  :D

---

### Post by enatiello on 2007-01-11
OK.  So does anyone know definitively the name of the script where the nfs shares listed in /etc/fstab should be mounted from?

---

### Post by pbardet on 2007-01-18
I have the same issue (nfs not mounting shares at boot time).

I took a look at /etc/rcS.d and noticed that the "mount -a" command (S35mountall.sh) is run before networking is started (S40networking).
S46mountnfs-bootclean.sh would be supposed to mount NFS shares, but I can't see any mount command in it. So I'm not sure exactly what happens here.

I recently switched from gentoo to Ubuntu and it used to work fine. I'm not really willing to switch back based on how much manual config is needed but right now, I'm upset NFS shares don't mount properly with Ubuntu and it seems nobody knows why. I've been looking around for 2 weeks now. I can't believe nobody else experiences this issue to become a priority with Ubuntu developpers.

---

