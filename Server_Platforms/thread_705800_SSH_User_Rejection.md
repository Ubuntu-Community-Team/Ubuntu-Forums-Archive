---
title: "SSH User Rejection"
date: 2008-02-23
forum: Server Platforms
---

### Post by tufcamman on 2008-02-23
Hi, I'm fairly new to linux and have a few questions.  I was logged into my 7.x server using SSH from my Windows computer using Putty.  I was going along my merry way making changes and then I logged out because I was done and now when I go to log in again using the same username as soon as I type in the password Putty closes.  If anybody knows why this is happening that would be great.  Thanks.

---

### Post by Sam Lars on 2008-02-23
Did you change any SSH stuff?

---

### Post by mrsteveman1 on 2008-02-23
Sounds like password authentication is still setup or it wouldn't even be asking for a password.

My guess would be that something in the ssh config changed, or perhaps some part of the authentication system on the linux box (includes PAM, the passwd file etc) changed for some reason.

---

### Post by p_quarles on 2008-02-23
Are you using denyhosts on the server, by any chance? If that is misconfigured, it can cause precisely this kind of behavior.

One thing to try here would be to use a better SSH client (PuTTY is okay, but it's not perfect). If you have a *nix machine from which you can login, or could create a virtual machine for this purpose, you will get more verbose output about the cause of the problem.

---

### Post by faulkes on 2008-02-23
Although I highly doubt it, could be that somehow the shell was changed.

I'd suggest booting into recovery mode and looking around the system, especially
the logs (/var/log/secure, /var/log/syslog, /var/log/messages)

Faulkes

---

### Post by k_grdn on 2008-02-24
Hi,

If you have access to the box then it's /var/log/auth.log you need to grep.

Also it will be best to trouble shoot from another linux box, connect ssh with a -vvv option and post the output.  This way you'll get some debug output to focus on.

If not start sshd in deamon mode on the linux box and then review the output when connecting from the putty host.

Daemon mode:

/etc/init.d/ssh stop

/usr/sbin/sshd -d

Regards,

k_grdn

---

