---
title: "ACL + XFS + SAMBA on Ubuntu 8.04 Server"
date: 2009-03-25
forum: Server Platforms
---

### Post by jonta on 2009-03-25
I am trying to setup ACL on my Ubuntu 8.04 server. I am running the x64 version of it.

So far i have:
apt-get install acl
added nt acl support = yes to the smb.conf

I tried adding acl to the xfs mount parameters in fstab but then the volyme was unable to mount.

When opening the share i have activeded acl on i get a security tab with the current permissions, but when changing them and clicking "apply" they dissapear again.

I have tried to search the forums and googeling but have not found anything. Is it that maybe some kind of parameter in fstab is needed but it's no "acl"

---

