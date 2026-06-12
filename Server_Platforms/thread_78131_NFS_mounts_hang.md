---
title: "NFS mounts hang"
date: 2005-10-17
forum: Server Platforms
---

### Post by mjpowersjr on 2005-10-17
Hello,

I am having a few issues with mounting nfs filesystems. I have a small fileserver in my house runny Hoary and two desktop clients running breezy. When the clients ran hoary, nfs worked just fine, now after upgrading, the clients hang for a very long time when mounting the drives. Eventually the drives are mounted, but it takes a very very long time. Before upgrading to breeze the mount time was almost instant. Also I have noticed, if i interupt the mount ( ctrl + c ) it can stop the hang, but the drive is mounted at this point. ( so it seems that it hangs after mounting). Below is a bit more system specific info that may be useful. Thanks in advance for any help.

Server kernel version (hoary): 
Linux version 2.6.11-1-k7 (buildd@mcmurdo) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Fri Feb 11 14:16:27 UTC 2005

Client1 kernel version (breezy):
Linux version 2.6.12-9-k7 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:47:52 BST 2005

Running dmesg on the clients after an attempted mount produces this error:
[4296293.596000] nfs warning: mount version older than kernel
[4296328.597000] portmap: server localhost not responding, timed out
[4296328.597000] RPC: failed to contact portmap (errno -5).

---

### Post by wylfing on 2005-10-17
Are you using the kernel module NFS server? If so, switch the userland NFS server.

---

### Post by mjpowersjr on 2005-10-17
Thanks for the quick response!

Yes,  I was using the kernel server. I have now switched to the userland server. I bet that was the problem. The only issue i have now seems to be a permissions issue. When trying to mount now, the serve reports this in the syslog:

Oct 17 22:40:03 localhost mountd[7498]: Unauthorized access by NFS client 192.168.0.1.
Oct 17 22:40:03 localhost mountd[7498]: Blocked attempt of 192.168.0.1 to mount /home

and th clients report:
mount: pserver:/home failed, reason given by server: Permission denied

I have never used the userland server before, is there somewhere else i must configure besides /etc/exports?

---

### Post by mjpowersjr on 2005-10-18
Looks like i found the problem. I have switched back to the nfs-kernel-server. The userland server was giving my lots of issues, and nothing seemed to make it better. It could of just been me (not much experience w. nfs) What I did do was, switch back to the kernel server & install the nfs-common ubuntu packages through synaptic on all the clients, now everythings very speedy :-)

---

### Post by LordHunter317 on 2005-10-18
The userland NFS server is slow and has been deprecated for essentially forever in favor of kernelspace.

I don't know what you were missing, but it looked like you were having portmapper issues, which would cause long timeouts.

---

### Post by wylfing on 2005-10-18
[QUOTE=LordHunter317]The userland NFS server is slow and has been deprecated for essentially forever in favor of kernelspace.
[/QUOTE]

I know, but sometimes when people get wierd lockups with the kernel server they can get functional NFS by switching to the userland server.

@mjpowersjr - Nice to know things are working now.

---

