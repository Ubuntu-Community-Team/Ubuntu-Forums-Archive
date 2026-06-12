---
title: "Home Directories - PAMMOUNT and SAMBA"
date: 2011-03-08
forum: Server Platforms
---

### Post by jtwood on 2011-03-08
Here is what I have:

A Samba Fileserver - Ubuntu Server 10.04
An LTSP Server - Ubuntu Server 10.04
A Windows Server 2008 R2 Active Directory Server

I'd like to mount the user home directories on login for both Windows sessions and LTSP sessions.  Believe it or not, I got the Windows part working easily.

I've been fighting with PAM MOUNT but I have had zero luck.

mount configuration from pam_mount.conf.xml
```
<volume fstype="cifs" server="192.168.98.90" path="IT" mountpoint="/testmount/" options="username=DOMAIN\\%(USER)" />
```

I've also tried variations with %(DOMAIN_NAME) and %(DOMAIN_USER) substituted.

What I always seem to get in the debug output on console from pam_mount is that the user is being set to test.user rather than DOMAIN\test.user - the mount then fails due to permissions on the fileserver (expected with the way the user name is being set)

The thing is, I am pretty sure that the permissions and the share are set up right...a manual mount works just fine:

sudo smbmount //192.168.98.95/IT /testmount/ -o user=DOMAIN\test.user


I am sure that there is something wrong somewhere, but I can't find it.  I am open to ideas.

I am using Ubuntu 10.04 and the pam_mount is merely from the default repos for lucid.  I don't think the problem is with Samba as I can mount the share manually.  The only configuration added to the pam_mount.conf.xml is the line I posted above.

Any ideas or suggestions feel free --- you could save a server's life.

---

