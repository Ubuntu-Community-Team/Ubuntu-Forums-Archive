---
title: "Edit ssh banner via non-ssh connection"
date: 2010-06-14
forum: Security
---

### Post by ld.4lpha on 2010-06-14
I have changed my sshd banner in /etc/motd:

```

user@client:~$ ssh ld4lpha@server
Custom banner message displays properly.
ld4lpha@server:~$

```However, I would also like to change the banner that someone sees if they attempt to use another method of connecting to my ssh server (telnet, for example).  Currently, this is what happens:

```

user@client:~$ telnet ssh_server 22
Trying server...
Connected to server.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu3

```Where do I edit the telnet/ssh banner, so it isn't so easy to fingerprint my os/ssh version simply by using something such as telnet?

Thanks!

LD

---

### Post by anomie on 2010-06-15
Here's a [thread](http://lists.debian.org/debian-security/2002/10/msg00318.html) on that topic. 

Short answer: 
[list]
[*] you modify the openssh source code
[*] this is arguably *useless* as a "security" mechanism
[/list]

By the way, "ssh banner" is a misnomer in this context. (There is an entirely different Banner directive.)

---

### Post by ld.4lpha on 2010-06-15
> **anomie said:**
> Here's a [thread]("http://lists.debian.org/debian-security/2002/10/msg00318.html") on that topic. 

Short answer: 
[LIST]
[*] you modify the openssh source code
[*] this is arguably *useless* as a "security" mechanism
[/LIST]

By the way, "ssh banner" is a misnomer in this context. (There is an entirely different Banner directive.)

Perfect.  Thanks for the link.

---

