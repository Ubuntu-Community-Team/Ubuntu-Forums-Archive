---
title: "Update to xenial aborted!"
date: 2016-02-29
forum: Ubuntu Development Version
---

### Post by DatOneLefty on 2016-02-29
i used the command do-release-upgrade -d
it downloaded stuff, then it said:

```
Calculating the changes

Error authenticating some packages 


It was not possible to authenticate some packages. This may be a 
transient network problem. You may want to try again later. See below 
for a list of unauthenticated packages. 


module-init-tools 




Restoring original system state


Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 



```
How can i fix this so i can install?

---

### Post by DatOneLefty on 2016-02-29
i fixed it by adding a file to my computer that allows the package!

---

### Post by raonyguimaraes on 2016-03-02
This solves the problem: 

create the file /etc/update-manager/release-upgrades.d/unauth.cfg as root and add the following.

[Distro]
AllowUnauthenticated=yes


[http://askubuntu.com/questions/425355/error-authenticating-some-packages-while-upgrade/426121#426121](http://askubuntu.com/questions/425355/error-authenticating-some-packages-while-upgrade/426121#426121)

---

### Post by Bucky Ball on 2016-03-02
*Thread moved to **Ubuntu Development Version**.*

As it looks like you've only just dipped your toe in here, just curious as to why you would want to upgrade to an unreleased version of Ubuntu? :-k

Enjoy the learning curve and expect the unexpected. All posts regarding 16.04 LTS go here. Good luck.

---

### Post by zika on 2016-03-02
> **raonyguimaraes said:**
> This solves the problem: 

create the file /etc/update-manager/release-upgrades.d/unauth.cfg as root and add the following.

[Distro]
AllowUnauthenticated=yes


[http://askubuntu.com/questions/425355/error-authenticating-some-packages-while-upgrade/426121#426121](http://askubuntu.com/questions/425355/error-authenticating-some-packages-while-upgrade/426121#426121)By no means a solution. Patch may be... ;)
You do not want to leave it that way.

---

### Post by kansasnoob on 2016-03-02
Was this an upgrade from Trusty to Xenial? Or from Wily to Xenial?

The latter worked OK for me during Beta 1 testing but the Trusty -> Xenial upgrade was borked:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1549067](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1549067)

---

