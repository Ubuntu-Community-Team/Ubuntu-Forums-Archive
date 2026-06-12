---
title: "Advice for setting up a fileserver (with multi-OS clients)"
date: 2009-11-21
forum: Server Platforms
---

### Post by danep on 2009-11-21
Hello all- I am setting up a small departmental server running the LAMP stack that will ideally be used as a file server. Clients will be a number of OSes including Windows XP/Vista/7 and Ubuntu. Ideally, the following two conditions should hold:

[LIST=1]
[*]Vista/7 and Ubuntu clients should be able to mount the share natively, without having to install any additional software or jump through too many hoops.
[*]I need to handle authentication via either CAS or a separate Kerberos server.
[/LIST]
I am aware of several filesystems and protocols such as nfs, WebDav, and Samba but am not sure which (if any- none seem to completely fit the bill) would be most appropriate given these constraints. Can anyone offer some advice? I would really appreciate it- I'd really love to continue using Ubuntu rather than have to switch to Windows IIS! :)

---

### Post by twidget on 2009-11-21
dunno about number 2 as I've never used either of them but Samba works fine on a mixed OS network. Mine hasy happily connected to Ubuntu, Kubuntu, Win 7 x64, Vista x64, and Win Xp 32 bit.

---

### Post by Vegan on 2009-11-21
LDAP might be a better choice than 2, this allows a bank of servers to use a single log-in.

---

### Post by Lars Noodén on 2009-11-24
> **danep said:**
> Hello all- I am setting up a small departmental server running the LAMP stack that will ideally be used as a file server. Clients will be a number of OSes including Windows XP/Vista/7 and Ubuntu. Ideally, the following two conditions should hold:

[LIST=1]
[*]Vista/7 and Ubuntu clients should be able to mount the share natively, without having to install any additional software or jump through too many hoops.
[*]I need to handle authentication via either CAS or a separate Kerberos server.
[/LIST]
I am aware of several filesystems and protocols such as nfs, WebDav, and Samba but am not sure which (if any- none seem to completely fit the bill) would be most appropriate given these constraints. Can anyone offer some advice? I would really appreciate it- I'd really love to continue using Ubuntu rather than have to switch to xxxx

Hey watch the language.  ;)  No need for you to threaten to destroy your own stuff.  ;)

Of those choices, look at Samba first.  It should be configurable to use  Kerberos authentication.

---

