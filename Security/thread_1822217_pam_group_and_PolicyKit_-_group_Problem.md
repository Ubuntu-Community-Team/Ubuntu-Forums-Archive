---
title: "pam_group and PolicyKit - group Problem"
date: 2011-08-10
forum: Security
---

### Post by ms99 on 2011-08-10
I have an Ubuntu 11.04 running with ldap authentication configured.

Login works fine. 

I use pam_group in /etc/security/group.conf with following line, to add groups to ldap-users.
*;*;*;Al0000-2400;user,adm,dialout,cdrom,plugdev,lpadmin,admin,sambashare

But if a user wants to alter settings (For example System->Administration->Login Screen->Unlock) in the Gnome Desktop, the policykit doesn't recognise the added groups,and so he need root/admin password to configure settings with the Gnome Desktop.

I discovered a weird thing:

logged in as userx gives the following:

userx@mymachine:~$ id
uid=11863(userx)  gid=100(users)  groups=100(users),4(adm),20(dialout),24(cdrom),46(plugdev),112(lpadmin),120(admin),122(sambashare),1000(user)

This seems to pam_group working right adding the configured groups to userx.

but if i make "id userx" I get:
userx@mymachine:~$ id userx
uid=11863(userx) gid=100(users) groups=100(users)

showing the groups says userx is not an admin:

userx@mymachine:~$ getent group admin
admin:x:120:user

But showing the groups of userx says he is! 

userx@mymachine:~$ groups
users adm dialout cdrom plugdev lpadmin admin sambashare user

So the questions:

Why does "id userx" and "id"(logged in as userx) give different results ?!? .
Why are there different results using "groups" and "getent  group admin".
How can I configure pam_group to set right group permissions, so that policykit can use it?

Thanks a lot.



What's going on here?

---

### Post by annunaki2k2 on 2011-10-17
Did you ever find a way to resolve this or the cause of the problem?

I'm experiencing a similar - if not the same - problem here in my office. We have LDAP working and are in the process of moving some machines from 10.04 to 11.04 (for the more stable evolution). At the moment, there is one user that logs onto one machine where she doesn't get the groups and yet anyone else that logs on to it appears to get the correct groups from LDAP. but also her account works on any other machines - it's a really frustrating little bug that seems to have no error messages logged relating to it.

Out of interest, do you have NSCD installed and running? I'm thinking it's NSCD's fault but I can't find the proof...

---

### Post by nicolasavru on 2011-10-28
I am also curious about this. Did you ever find a solution?

---

