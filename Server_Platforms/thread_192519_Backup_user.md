---
title: "Backup user"
date: 2006-06-08
forum: Server Platforms
---

### Post by ddeflyer on 2006-06-08
I am working on creating a backup system on a server I am running. I want to make it so that this user (the backup user) can have read only access to everything on the system. I want it to only have read access, so sudo'ing to root or something is not going to work. In a perfect world I would also have /etc be not readable, but that isn't as required.

So is there anyway to do this without going beyond the basic *nix permisions setup?

---

### Post by ximok on 2006-06-09
Posix ACLs would be the solution that I would see working for you.  I have never implemented Posix ACLs in Ubuntu. 

[http://www.wlug.org.nz/AccessControlLists](http://www.wlug.org.nz/AccessControlLists)

In a nutshell:
Make sure you have universe as one of your repositories

apt-get install acl
edit your ftab file to contain "acl" as one of your options (this tells the kernel to look for ACLs in that filesystem)
```
/dev/sda1    /     ext3   defaults,acl   0   0
```
use getfacl and setfacl to do your acl permissions. 

If you get "Operation not permitted" errors, then you need to fix your fstab table.

oh, once you have that installed do a "man getfacl" and "man setfacl" to get yerself acquainted.

The eiciel package is also nice for nautalis support, but I don't recommend using it till you understand the posix acl system first.

---

