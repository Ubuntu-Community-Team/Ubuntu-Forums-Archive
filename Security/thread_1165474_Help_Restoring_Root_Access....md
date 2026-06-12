---
title: "Help Restoring Root Access..."
date: 2009-05-20
forum: Security
---

### Post by svtguy88 on 2009-05-20
So, somehow my administrator account got taken out of the sudoers list.  Anytime I try to use 'sudo' and enter my password (while logged in as admin), I get an error complaining that I'm not in the sudoers file.  

Also, I can't open Synaptic, or anything that would normally require sudo access.  I'm pretty sure that somehow the administrator account got taken out of the "admin" group in the Users and Groups menu, but I now have no way to get into that menu to change it...

Ideas?  Can I log in as root?  I don't remember if I enabled root login or not, and if I did, I have no idea what the password is....

Worst part is, the administrator account that I created is the only admin account, so I have no way to install or change anything until this is figure out....

---

### Post by bodhi.zazen on 2009-05-20
Boot to recovery mode, this will give you a root shell.

At the command line enter :

```
adduser <username> admin
```

change "<username>" to your log in name.

Then either reboot or exit the shell and continue booting.

---

### Post by svtguy88 on 2009-05-20
Just fixed it before seeing your post.  Thanks for your reply.

I ended up booting to the live cd, then mounting my hd and editing /etc/group, putting the correct users back in the admin group.

---

### Post by bodhi.zazen on 2009-05-21
> **pkmgarf said:**
> Just fixed it before seeing your post.  Thanks for your reply.

I ended up booting to the live cd, then mounting my hd and editing /etc/group, putting the correct users back in the admin group.

Awesome :)

That is what I do, but it is a bit more complicated for new users.

---

