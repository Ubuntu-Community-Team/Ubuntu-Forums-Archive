---
title: "Mount disk on more virtual machine"
date: 2010-03-23
forum: Virtualisation
---

### Post by MicKAngel on 2010-03-23
Hi everyone, just subscribed here cause I have a problem I wish to solve.

I installed a Ubuntu Karmic server version, with Xorg libraries. I put that installation as a host for virtual machines. Inside it I installed (with KVM) 2 virtual machines (Ubuntu Karmic server), for instance vm1 and vm2. On host I built a software raid device, /dev/md2.
I want to forward /dev/md2 to vm1 and vm2. Easy till now. I can forward without any problem. Problems come when I mount that partition. In vm1 and vm2 appear /dev/sdb, but it is the partition, not the disk (I cannot forward disk, cause I need to forward the partition post mirroring).
When I mount the partition ONCE it works without any problem. When I mount in other vm (or the host) the partition I haven't syncronized data.

Now, is there a way to mount that partition on both vm and host? Or any other configuration I should use to let this work?

I appreciate any help.

---

### Post by HermanAB on 2010-03-23
No you cannot mount a disk twice, since it will lead to corruption of the disk.  If you want to access data in multiple places, use a file server such as NFS or FTP.

---

### Post by Exca on 2010-03-23
Hi MicKAngel, and welcome on this forum ;-)

Mounting two times the same disk on two different machines simultaneously should be very cool, but the problem is that 2 systems can not use simultaneously one filesystem. You must have one machine dedicated to the disk acces.

I was working on a similar issue, the best solution I found is to mount a partition on the Host, and to use it thanks to an ssh connection. On all the VM thatneed to use this shared disk, I've installed SSHFS and added the disk manually in my two /etc/fstab.

You can easily find some good tutorials on that.
Hope this help,

Exca.

---

### Post by MicKAngel on 2010-03-24
Thanks for replies.
I admit I'm just a little more newbie for this stuff, but I understood what you mean Exca.
But does it use ethernet connection for transport data between host and virtuals? I found another workaround, using host as NFS server and share a directory (the mounted partition), but I don't want to use ethernet connection for this. Using NFS it's bad too, cause in disks forwared I should put PostGre data.

I appreciated it anyway your helps

---

### Post by Exca on 2010-03-24
I've find something interesting on it !

There is one filesystem supporting concurrent access to the same partition by multiple machines : Global File System (GFS). This filesystem is designed to work on clusters, but there is a way to use it on a "local" disk.

More informations on this page : [http://en.wikipedia.org/wiki/Global_File_System](http://en.wikipedia.org/wiki/Global_File_System)

It seems to be a very powerful filesystem, but also very hard to configure !

More informations here, [http://knowledgelayer.softlayer.com/questions/443/GFS+howto](http://knowledgelayer.softlayer.com/questions/443/GFS+howto) about how to use it on a network, but I cannot find how to run it on a "local" disk.

Good luck ;)

---

