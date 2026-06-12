---
title: "Actions requiring root privileges asks for wrong user"
date: 2011-05-24
forum: Security
---

### Post by robmc2049 on 2011-05-24
In our group we use NIS and have a group set up called netadmin which is given root privileges on each machine.  Each machine also has a localuser called localuser created and used during installation.  When logged in as a member of netadmin, attempting any action that requires root privileges (e.g. installing software in Ubuntu Software Center) results in a prompt asking for localuser's password, not the current user's password.

Does anyone know the cause? Configuration issue or Ubuntu issue? We can get around it, but it's really annoying.

thanks

---

### Post by robmc2049 on 2011-05-24
Found a permanent fix.  Added netadmin group to AdminIdentities in /etc/polkit-1/localauthority.conf.d/51-ubuntu-admin.conf.

---

### Post by bodhi.zazen on 2011-05-24
You can look at the sudo manual 

[http://www.gratisoft.us/sudo/sudoers.man.html](http://www.gratisoft.us/sudo/sudoers.man.html)

See the runas and runaspw

---

