---
title: "Enabling root login from a tty, NOT for someone logging in via ssh"
date: 2008-07-15
forum: Security
---

### Post by Yann2 on 2008-07-15
Hello, 

My question is regarding password authentication in Ubuntu. My current security policy is: no passwords, at all, only use SSH keys.

But, in case something bad happens (wrong permission on the sudoers, wrong permission on the authorized_key file, whatever), I would like to be able to log in without having to reboot the server into single mode.

My idea is, I want one root password, the same for all my servers and VMs; only I want people to be able to use that root account *only* if they are directly connected to the server via a keyboard and a screen directly plugged in.

So, a user connecting via SSH should *not* be able to do su - root, enter the root password, and be logged in as root.

I've noticed that in /etc/pam.d/login:

# Disallows root logins except on tty's listed in /etc/securetty
# (Replaces the `CONSOLE' setting from login.defs)
auth       requisite  pam_securetty.so

But I don't know how to configure /etc/securetty to do what I want...
Any help would be much appreciated!

---

### Post by forger on 2008-07-15
You can disable the root login via ssh for all users
edit /etc/sshd_config

add the line:
> PermitRootLogin no

then: sudo /etc/init.d/ssh restart

I think you're also looking for the file **/etc/security/access.conf**
man access.conf

here's a nice guide:
[http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html](http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html)

---

### Post by Yann2 on 2008-07-15
Thanks, having a look, not sure it would do the job, as I want to filter by type of terminal instead of by remote address...

yhamon@roller:~$ who
yann     tty1         2008-07-15 06:02
yhamon   pts/0        2008-07-15 06:02 (10.0.10.69)
yhamon   pts/1        2008-07-15 06:02 (localhost)
yhamon   pts/2        2008-07-15 06:04 (10.0.0.163)

I don't understand how the terminals pts/* are able to su - root anyway, pts/0 doesn't seem to be in /etc/securetty? :confused:

---

