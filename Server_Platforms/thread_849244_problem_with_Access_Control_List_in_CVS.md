---
title: "problem with Access Control List in CVS"
date: 2008-07-04
forum: Server Platforms
---

### Post by elektro_komesar on 2008-07-04
Hi,
I have installed cvs, version 1.11.22. However, this version has no support for ACL (Access Control Lists). 
I have found some patch (cvsacl-1.2.5 for cvs 1.11.22). However, if you want to apply this patch, cvs has to be installed manually (and I have installed it using apt-get install cvs), because, there are some files which need to be copyed to CVS source directory.
Can anybody help me with this? 
If I uninstall (apt-get remove cvs) it`s uninstall cvsd also.
Do I need cvsd at all if I install cvs from source???
I need to access cvs repository using TortoiseCVS (from remote computer(s)). I have installed cvs, cvsd and inetd deamon, and everything working just fine, but user`s control has to be established, so I was thinking of using acl.
I don`t know what to do any more, I try to install cvsnt but documentation (some user guide for linux install) does not exists.
Anybody has any experience with any of this tools???

---

### Post by naughtykid on 2008-09-10
cvsnt is manage by a corporation, I guess that's why there's few documentation over it. If you need technical support, you pay for it. That's how they works.

Anyway, acl in cvs is a pain too. I'm actually setting up a cvs server using the cvsacl like you do. Having some issues keep the cvs server up and running. You manage to get the services up?

---

