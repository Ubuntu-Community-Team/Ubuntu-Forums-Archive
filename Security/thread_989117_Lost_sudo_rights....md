---
title: "Lost sudo rights..."
date: 2008-11-21
forum: Security
---

### Post by fgeorges on 2008-11-21
Hi,

  Surprisingly, I do not have the sudo rights anymore.  The only thing I can think of is that I mixed up options when trying to change the groups I belong to: instead of adding a new group, I set the comprehensive list of groups...

  Is there anything I can do except reinstall the system?

  Regards,

-- 
Florent Georges
[http://www.fgeorges.org/](http://www.fgeorges.org/)

---

### Post by cdenley on 2008-11-21
> **fgeorges said:**
> Hi,

  Surprisingly, I do not have the sudo rights anymore.  The only thing I can think of is that I mixed up options when trying to change the groups I belong to: instead of adding a new group, I set the comprehensive list of groups...

  Is there anything I can do except reinstall the system?

  Regards,

-- 
Florent Georges
[http://www.fgeorges.org/](http://www.fgeorges.org/)

Boot into recovery mode, select "root shell prompt", run
```

adduser fgeorges admin

```

---

### Post by Sarmacid on 2008-11-21
If you want to go back to the group you were in, use the root account to change your group. If you just want to use sudo again, use the root account or boot with a live cd and add yourself to the /etc/sudoers file. Make sure you make a backup of the file before modifying.

---

### Post by lswb on 2008-11-21
Boot into recovery mode and use this command

usermod -a -G admin your_user_name_here

---

### Post by fgeorges on 2008-11-21
> select "root shell prompt"

Didn't know this one.  Everything's fine now, thanks to you and other ones that answered!

-- 
Florent Georges
[http://www.fgeorges.org/](http://www.fgeorges.org/)

---

