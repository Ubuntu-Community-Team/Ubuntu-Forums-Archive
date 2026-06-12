---
title: "Sudo issue with NIS (QAS) groups"
date: 2012-04-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Thylex on 2012-04-13
Hi,

We're experiencing issues with sudo and accesses granted via groups defined in NIS. We are using VAS/QAS as NIS proxies, but the hosts are setup as normal NIS clients.
We have the same sudoers file with the same setup on 10.04 and it works fine there.
"id -a" shows all the right group memberships, "groups" shows all the right memberships, ypcat groups works fine, no issues with logging in on console or X, no issues with NFS access.
To make it even more fun, sudo-access tied to netgroups work just fine and accesses tied directly to usernames work fine. It's just when it's tied to a group  that it doesn't work.

Has anyone seen anything like this? Or have any advice?

---

### Post by NHclimber on 2012-04-13
This is pretty much a shot-in-the-dark but the fact that it only happens with groups would seem to indicate that it has to do with the funky way that QAS matches groups for sudo (ie, with @)  [http://rc.quest.com/topics/sudo/howto.php#ex](http://rc.quest.com/topics/sudo/howto.php#ex)

Anyway, another place to ask would be here [http://allthingsunix.inside.quest.com/forum.jspa?forumID=1214](http://allthingsunix.inside.quest.com/forum.jspa?forumID=1214)

---

