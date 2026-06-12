---
title: "lock skype or other apps"
date: 2019-04-26
forum: Security
---

### Post by iman24sh on 2019-04-26
hi  Ive just installed Skype and now i want set a Passcode to ask when i want to open Skype. (like telegram, in telegram you can set a passcode and whenever you open telegram you need to enter that).

i've search on Google for any application to lock applications in Linux but couldn't find anything ... is it really true??? in Linux we cant lock applications? (sorry for my English...)

---

### Post by TheFu on 2019-04-27
There are multiple solutions to this, using normal userid/groupid permissions controls.  Work through a tutorial if you don't understand how.

Solution A:
You can use groups to achieve this, but it won't be seamless.

Create a new group. Add the userids you want to have access to this group.  Change the permissions on they skype executable so that only members of that group can run it.  I don't use skype, but suspect 450 would be the permissions.  This would limit eXecution to only the members of the group.

If you wanted to force that a password be provided, then use gpasswd to get a password on the group.  I've never seen this used in the real world.

Solution B:
Use sudo to force users to access a different userid to run the program.  Create a new userid, setup the file permissions for skype so only that userid can run the program.  Setup the sudoers file so that your userid can change to the other userid through sudo.  The sudoers manpage explains how.  To make running skype under the alternative userid easier, I'd setup an alias with the full sudo -u command.

This solution could also be used with A, using sudo -g to force access to another group that the userid isn't a member. If the userid is a member, no need for sudo.

WARNING, running GUI programs through sudo is not advised because GUI programs tend to create config files owned by the userid. If those config files are shared with any other userid, permissions failures are likely.  Using sudo -H is a workaround for the userid issue.  Don't know if this will help if changing only the groupid to a group that the userid isn't a member of.  If the userid is a member of the group, no issues should happen.

---

