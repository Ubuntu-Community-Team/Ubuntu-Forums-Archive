---
title: "Understanding NIS Help..."
date: 2007-09-18
forum: Server Platforms
---

### Post by knichel on 2007-09-18
I have installed NIS in a lab environment.  I have a few questions...

1)  When the users try to change their passwords using yppasswd, they get an error "yppasswdd not running on master host".  According to all docs I have read, it looks as though yppasswd should be in /etc/init.d/yppasswdd, but the only one I find is in /usr/sbin/rcp.yppasswdd.  Any suggestions?  

2)  I created a bunch of users on my NIS master. They can log in and save docs via nfs just fine.  The NIS users do not have access to the audio on the local machine.  If I manually edit the local /etc/group file to include their username to the audio group, they have sound.  This seems counterintuitive.  Why do they not get it via NIS?  They are in the audio group on the server.  How do I fix this or is manually editing each workstation t he only way?

3)  There are occasions where I want to allow users to install/configure something (ie run using sudo).  Can I create a NIS user on the master and allow that user to have sudo priv's on the workstations?(how?)  I would then change the password on the server when I want them to log in and change it back when i do not want them to log in to that account.


Thanks for taking the time to reply.

Mike

---

