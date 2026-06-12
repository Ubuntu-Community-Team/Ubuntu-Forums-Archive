---
title: "ACL Server 10.04"
date: 2011-01-24
forum: Server Platforms
---

### Post by bearly230 on 2011-01-24
I've installed the acl packages.

I'm needing to have acl running on the /home directory for groups. I've read several help files and they all say to put the acl option in fstab on the /home label line.

What I need to know is for Server 10.04 how do I add a mount for home or where I need to put in the acl option.

Thanks in advance.

---

### Post by wongo888 on 2011-01-24
I added acl on a CentOS server last week. We put the acl on the root in /etc/fstab and every other dir inherited it, including /var/www where we needed it. It was pretty straightforward.

---

