---
title: "SSH Connection"
date: 2009-10-21
forum: Security
---

### Post by slydevil22 on 2009-10-21
What is the best way to secure my SSH connection on Ubuntu I am new at this and really need some great ideas.
 
Thanks

---

### Post by dominiquec on 2009-10-21
Read [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by Agent ME on 2009-10-22
Set strong passwords for your users, or disable logging on with a password over SSH and use SSH keys only.

---

### Post by kevdog on 2009-10-22
Oh no -- not a rehash of this same old topic?

---

### Post by zer0x on 2009-10-22
Hi,

Kevdog has a point, there are a million and one guides on this out there! (man 1 sshd)

Here is a brief summary, by no means comprehensive:

Use very secure passwords (or ideally ssh private/public keypairs).

Disable root logins (/etc/ssh/sshd_config)

```
PermitRootLogin no
```

Make sure Protocol is 2, UsePrivilegeSeperation is yes, and StrictModes is yes (these should be the default in ubuntu).

Prevent brute force attacks by either rate limiting the connection:

```
ufw limit ssh/tcp
``` (man 1 ufw)

Or, using additional software that will block IP's based on failed authentication attempts:

[http://www.fail2ban.org]("http://www.fail2ban.org")
[http://denyhosts.sourceforge.net/]("http://denyhosts.sourceforge.net/")

(both in the repo's).

You could change the ssh listening port from the default (22), but that is not very friendly.

Keep your ssh daemon (& system) up to date!

HTH

zer0x

---

