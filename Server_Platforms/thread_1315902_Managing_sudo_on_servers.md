---
title: "Managing sudo on servers"
date: 2009-11-05
forum: Server Platforms
---

### Post by fackamato on 2009-11-05
Hi guys,

I've been given a project where I'm supposed to secure several servers running AIX in terms of SSH and sudo (SSH comes after sudo's finished). We have different groups running different applications on these servers, and they all need different permissions and reasons to use sudo.
I want it to be easy to maintain so I was thinking of having one master /etc/sudoers file somewhere, and when that gets updated, just push it out to all the servers, perhaps weekly with crontab. Information in the master sudoers file that doesn't apply to the server it's on (such as groups that doesn't exist, etc) shouldn't be a problem unless I've missed something, I suppose.

I also need to find out what permissions one would need to run/use the applications so I know what to add in the sudoers file. These apps are Tivoli, DB2 etc. 

How would you do it, would you do it differently and if so, why?

Cheers,

M

---

### Post by puppetslave on 2009-11-07
Puppet would be a possible solution to centrally manage your ssh and sudo configurations, although whether it works on AIX is another question.

---

### Post by fackamato on 2009-11-07
> **puppetslave said:**
> Puppet would be a possible solution to centrally manage your ssh and sudo configurations, although whether it works on AIX is another question.

Unfortunately it doesn't. My initial idea is to, as I mentioned, have a centralized master sudoers file on a server somewhere, and have a cronjob rsync (or scp or something) that over to all the machines. I wonder if this is the best solution.

---

