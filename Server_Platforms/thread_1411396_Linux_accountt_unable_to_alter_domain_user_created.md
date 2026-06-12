---
title: "Linux accountt unable to alter domain user created files."
date: 2010-02-19
forum: Server Platforms
---

### Post by Pro_D on 2010-02-19
The problem is that I need the linux user to be able to manipulate files created by the windows domain users.

The solution seems to be to have the users within the same group.

The server is openldap+samba PDC.  I mostly use phpldapadmin to manage the domain.  Webmin for shares.  Mostly linux command line utilities or GUI tools via VNC to manage the local file system, linux users/groups, etc.

I have tried creating a linux group (with linux user added to it) and then mapping a domain group to that linux group.  Problem is that none of the other domain accounts are able to act as part of that group (access denied).  Also only phpldapadmin indicates that any of the domain users are members of the group.

On the other hand (this is where I am now) I have tried adding the linux account to the domain group via 'usermod -a -G <groupname> <username>'.  I get no error which I would get if I used a non-existent group however the linux user cannot manipulate (write to) files marked for that group.

I should note that there is a domain account that corresponds with the linux user account, pretty sure it was automatically created when I setup the openldap+samba.  Also I have the shares set to maintain group id on new files (chmod g+s).

---

