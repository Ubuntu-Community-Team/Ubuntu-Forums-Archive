---
title: "sudo and ssh not working after upgrade"
date: 2010-07-27
forum: Server Platforms
---

### Post by rsteinmetz70112 on 2010-07-27
I have a server that started out at 8.04 LTS was upgraded to 8.10 and to 9.04. When I upgraded to 9.04 sudo and ssh stopped working.

Fortunately I have a root account and can login as root or su to root.

I suspect this is the result of changes I made to nsswitch.conf and pam.conf to get winbind working.

I was hoping for a fix by upgrading to 9.10, but that didn't work. I want to upgrade to 10.04 LTS, and stay there but I think need to resolve this first.

auth.log reports failed password for ssh attempts and authentication failed for sudo.

I am at a loss to determine where the problem is and how to track it down.

---

### Post by CharlesA on 2010-07-27
Do you use password logins for SSH?

If it's spitting back authentication failure, you could try resetting your user's password by using the *pwd username* command.

---

### Post by rsteinmetz70112 on 2010-07-27
The users passwords work to login so the password file (actually shadow)should be fine.
The main user (me) can login in using my password, if I try to sudo, it asks for my password. I give it again, but it doesn't work. Same thing when starting Update Manager or Synaptic.

I can open a window and su to root and use apt-get.

---

### Post by cdenley on 2010-07-27
```

id
getent group admin
sudo grep '^[^#]' /etc/sudoers

```

---

