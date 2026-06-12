---
title: "automounting not working on ubuntu server"
date: 2008-03-14
forum: Server Platforms
---

### Post by kvonblohn on 2008-03-14
Hi,  this is my first post, so please bare with me.  I have an Ubuntu 7.10 LAMP server running that i want to have auto mount the users home directories.  Directories are shared via NFS on a solaris 10 box, and authentication is via NIS.  I have installed portmap, nis, nfs-common, and autofs, however it fails to mount the nfs shares at logon.  NIS authentication works, and I can mount the shares manually.  

I have used this technique to automount home directories for 25 lab computers running Ubuntu 7.10 desktop with no problem.  I have even cross checked the configuration files on the server against the ones on a working desktop machine, and they are the same.

I have even used the workaround for the autofs, and still nothing on the server.

Does anyone have any what might be different on the server vs the desktop to cause this?  Any help would be greatly appreciated.

Thanks!

---

### Post by wizard10000 on 2008-03-17
> **kvonblohn said:**
> Hi,  this is my first post, so please bare with me.  I have an Ubuntu 7.10 LAMP server running that i want to have auto mount the users home directories.  Directories are shared via NFS on a solaris 10 box, and authentication is via NIS.  I have installed portmap, nis, nfs-common, and autofs, however it fails to mount the nfs shares at logon.  NIS authentication works, and I can mount the shares manually.  

I have used this technique to automount home directories for 25 lab computers running Ubuntu 7.10 desktop with no problem.  I have even cross checked the configuration files on the server against the ones on a working desktop machine, and they are the same.

I have even used the workaround for the autofs, and still nothing on the server.

Does anyone have any what might be different on the server vs the desktop to cause this?  Any help would be greatly appreciated.

Thanks!

There's no real difference between a Gutsy LAMP server and a desktop machine except the kernel.  If you can mount the NFS shares manually then the problem is autofs and I hate to say it, but if they were configured the same they'd work, honest  ;-)

If you can mount the shares manually the Solaris box is configured correctly so let's look at the LAMP server.  autofs needs two configuration files in order to run, /etc/auto.master and another config file that we'll specify in auto.master.   Let's call it /etc/auto.solaris

Okay.  We set up /etc/auto.master like this -

```
#
# $Id: auto.master,v 1.4 2005/01/04 14:36:54 raven Exp $
#
# Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).
#/misc	/etc/auto.misc --timeout=60
#/smb	/etc/auto.smb
#/misc	/etc/auto.misc
#/net	/etc/auto.net
/mnt  /etc/auto.solaris --timeou=300 --ghost
```

then we create a text file called /etc/auto.solaris that looks like this -

```
#
solaris 	-fstype=nfs, -rsize=8192, wsize=8192, soft, timeo=15, rw  ip.address.of.solaris:/location/of-share
```

The NFS share will mount at /mnt/solaris

Hope this helps -

---

