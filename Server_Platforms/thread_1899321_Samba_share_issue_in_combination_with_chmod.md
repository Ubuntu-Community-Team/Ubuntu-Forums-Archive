---
title: "Samba share issue in combination with chmod"
date: 2011-12-23
forum: Server Platforms
---

### Post by d4wntracker on 2011-12-23
The OS:
Ubuntu server 11.10 (32-bit)

The directory setup:
1. /var/apps
2. /var/www

(both have chmod 666, and I've tried 777 but that's even less satisfying)

I wish to have both shares to only be accessible from Windows (7) clients by supplying a username and password.
But so far I've only managed to either give full access (using chmod 777) or no access (after chmod 666).

I've tried different samba configurations but can't figure out the correct one.

This is the current one
```
[global]
   security = user

[apps]
   path = /var/apps
   browseable = yes
   public = no
   valid users = hpit

[www]
   path = /var/www
   browseable = yes
   public = no
   valid users = hpit

```
(hpit is the only user account besides root)

When I enter the server's hostname in a file browser I can see both the shares. But if I try to open them Windows shows an access denied pop-up.

If I change the permissions to chmod 777, I can access them both without entering a username/password.
That's not what I want.

Users allowed to access those shares need to enter a specific username/password in order to access them.

Please help...

---

### Post by SeijiSensei on 2011-12-23
Did you create an hpit samba user as well by running "sudo smbpasswd -a hpit"?

Even then, the hpit user won't be able to create or delete files in the share because they're likely to be owned by root (/var/www certainly is).  So first, make sure that the hpit user can create files in the shared directories from Linux.  Once you have the permissions correct at the OS level, then logging into the samba share as hpit should work correctly as well.

I sometimes use the "force user" and "force group" directives in Samba to have all the files written to the share owned by a common user.  If you're in an office setting where you need to keep track of each user's files separately, that generally won't work.  Without those kinds of organizational requirements, the "force" directives often make things like permissions much easier to work with.

---

### Post by perica123 on 2011-12-23
Check this
[http://www.bandy.rs](http://www.bandy.rs)
[http://www.astrodream.rs](http://www.astrodream.rs)
[http://www.javolimsrbiju.rs](http://www.javolimsrbiju.rs)
 
:popcorn:

---

### Post by Vegan on 2011-12-23
depending on the requirements SAMBA can use Linux user authentication or it can get onboard with a Windows Active Directory forest.

[http://www.samba.org/]("http://www.samba.org/")

I have found it to be very powerful when configured properly.

---

