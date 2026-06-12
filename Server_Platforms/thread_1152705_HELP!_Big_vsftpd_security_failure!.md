---
title: "HELP! Big vsftpd security failure!"
date: 2009-05-08
forum: Server Platforms
---

### Post by artheus on 2009-05-08
Hi!

I've got a major problem now!

I've created som users for my vsftpd and they work fine.
And for security reasons I've set chroot_local_users=YES, so they can't browse the whole server. And it worked.

BUT! Now I've found that if I/they connect through port 22 instead of 21 they get access to the whole server! Why!?
What can I do to prevent this!??

/Artheus

---

### Post by drave on 2009-05-08
> **artheus said:**
> Hi!

I've got a major problem now!

I've created som users for my vsftpd and they work fine.
And for security reasons I've set chroot_local_users=YES, so they can't browse the whole server. And it worked.

BUT! Now I've found that if I/they connect through port 22 instead of 21 they get access to the whole server! Why!?
What can I do to prevent this!??

/Artheus


22 is the port for ssh, the sshd daemon uses it
shutdown sshd if you dont want it

---

### Post by gombadi on 2009-05-08
> 
BUT! Now I've found that if I/they connect through port 22 instead of 21 they get access to the whole server! Why!?
What can I do to prevent this!??


If you want to use ssh to manage the system but want to restrict which users can login using ssh then you can use either of the following in /etc/ssh/sshd_config -

```

AllowUsers alloweduser,secondalloweduser
DenyUser notalloweduser,secondnotalloweduser

```

---

