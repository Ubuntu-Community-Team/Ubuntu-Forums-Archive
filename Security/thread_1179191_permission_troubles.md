---
title: "permission troubles"
date: 2009-06-05
forum: Security
---

### Post by megarainman on 2009-06-05
I created an Ubuntu fileserver who's attached to a Windows 2003 domain controller.   Everything is working fine with ACL's except the following thing keeps my brains busy...  

When a certain user (domainuser1) create a folder in a certain samba folder then the owner of the folder become for example domainuser1 and the group becomes "domain users".  

The result of this is that I can't access the folder anymore with my local account on the fileserver.  I have a cronjob who start an rsync process with a local Ubuntu user to backup everything.  But off course... the folders created by Samba users are permission denied.  

Now I do a chown with the local user to all the folders I want to backup using rsync.... but that's not the way it should be done.  Can anyone help me how I can manage that I have allways the right to enter any folder even if I am not the creator of it?

Thanx in advance!

---

### Post by koenn on 2009-06-05
if you're already using ACL; it should be possible to add a default group to all newly created files/folders, and with a (local) account in that group, you should be able to do the backups -- I think
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm)

---

### Post by megarainman on 2009-06-07
Hello Koenn,

thanx for the fast reply!  I found another solution for the problem by adding the local administrator to the group and then set a chown -R g+s over all the data I want to backup.

---

