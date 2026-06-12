---
title: "Automounter not mounting NFS"
date: 2010-05-19
forum: Server Platforms
---

### Post by JoelCant on 2010-05-19
Hi,

I have just upgraded my 2 servers to 10.04 LTS. 

After a couple of hours getting the new likewise open working again, and finding out that LW now doesn't support Samba.. but thats a different issue.

Users authenticate via Likewise against AD, but:

My automount system seems to have stopped working.

The fileserver has the NFS exports as 

/home/DOMAINNAME   10.0.0.0/16(rw,sync,no_subtree_check)

on the client machine I am testing with I have:

/etc/master:

/home/DOMAINNAME  /etc/auto.home

/etc/auto.home:

* fstype=nfs,nolock,nosuid      10.0.3.10:/home/DOMAINNAME/&

But when I log into the client via ssh

Could not chdir to home directory /home/DOMAINNAME/testuser: No such file or directory

The share mounts fine manually.

Anyone any ideas, I can't even find any logs for automounter.

Joel

---

