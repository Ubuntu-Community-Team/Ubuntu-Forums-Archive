---
title: "Problems LDAP and SSH"
date: 2010-03-17
forum: Server Platforms
---

### Post by jardim on 2010-03-17
Hi all,

I have been a problem to connect trought SSH with LDAP`s users. My LDAP is work well, but I can't connect SSH. I get a error message: Permission denied, please try again.

In my AUTH.LOG I have the follow message:

sshd[3446]: error: Could not get shadow information for xxxxxx
sshd[3446]: Failed password for xxxx from 127.0.0.1 port 53914 ssh2

Some idea?

Thanks.

---

### Post by KB1JWQ on 2010-03-17
Put files ldap as the precedence in /etc/nsswitch.conf for the appropriate sections, generally users and passwords, possibly shadow as well.  

Ensure that ldap.conf is correct.  It should "just work."

---

### Post by jardim on 2010-04-16
Ok All,

I got. I needed put UsePAM yes into sshd_config file.

Thanks.

---

