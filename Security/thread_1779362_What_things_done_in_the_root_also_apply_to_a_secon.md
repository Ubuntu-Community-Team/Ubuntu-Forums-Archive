---
title: "What things done in the root also apply to a second user"
date: 2011-06-10
forum: Security
---

### Post by toolmania1 on 2011-06-10
What things apply to a second user that also apply to root?  
 
For example, when AppArmor is set up, does this apply to all users on the system?  
 
Does ClamAV scan all users when ran logged in as root?  Does ClamAV scan all users when ran logged in as a user?
 
Is there a way to get Firefox settings to apply to all users on a system?  ( Right now, I have to go in on each user and add my add-ons like NoScript, AdBlock plus etc. and also set up FIPS and my browsing history settings. )
 
Is there a way to navigate to the second user's information ( folders / files ) from a root user?
 
Can files be shared from root to a second user?

---

### Post by toolmania1 on 2011-06-10
I think I found one answer.  

[https://wiki.ubuntu.com/SecurityTeam/Policies](https://wiki.ubuntu.com/SecurityTeam/Policies)

**Permissive Home Directory Access**

By default, Ubuntu is designed to allow users to easily share files and help each other ([see bug 48734]("https://bugs.launchpad.net/bugs/48734")).  To support this, each user's default home directory is readable by all other users.  Private files could be kept in the "Private" sub-directory, where access permissions can be set to limit access by other users (mode 0700).  If restrictive home directory permissions are a priority for your system, please investigate the /etc/adduser.conf file for adjusting various settings when creating new users, including the default permission mask for newly created home directories.

---

