---
title: "ssh on two ports with different security"
date: 2008-08-02
forum: Security
---

### Post by gyterpena on 2008-08-02
Hi

I have ssh running on two ports 993 for wan and 22 for lan works fine.
Now I want to restrict 993 to public key only and leave 22 as it is. 

Thanks

edit
Could not figured it out, ended up with dropbear on port 993 and sshd on 22

---

### Post by kidders on 2008-08-04
Hi there,

You don't need to run two different SSH server applications ... two instances of the same one would have been fine. That way, at least you're only exposing yourself to one application's security issues.

There is a much more straightforward solution though. You could ignore the fact that WAN connections are always on port 993, and LAN connections on 22. Instead, use OpenSSH's "Match" keyword to turn authentication by password on for local addresses.

There's a list of other things you can do with "Match" blocks in sshd_config's man page.

---

### Post by gyterpena on 2008-08-04
Thanks adding this at the end of sshd_conf worked.
Match   Address XXX.XXX.XXX.XXX
	PasswordAuthentication yes

---

