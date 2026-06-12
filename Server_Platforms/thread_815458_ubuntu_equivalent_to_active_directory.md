---
title: "ubuntu equivalent to active directory"
date: 2008-06-01
forum: Server Platforms
---

### Post by mohenjo on 2008-06-01
What would the Ubuntu version of "Active Directory" be, and where might I go to find some good documentation for setting it up an creating a domain?

---

### Post by quelx on 2008-06-01
AD intergration

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

Domain controller

[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

---

### Post by mohenjo on 2008-06-01
Would those solutions be used to create a domain and directory without having Windows servers set up at all?  Just wondering if that's the way to go if I'm building a network from all ubuntu machines.

---

### Post by quelx on 2008-06-01
Not exactly...  As I understand it, AD is a tool to manage resources in a domain, Linux can do this but it uses other tools to accomplish this task rather than the monolithic route AD takes.  This provides alot of flexibility but at the same time complexity especially in the initial setup.

There is alot of information out there to implement this.

google:*linux active directory*

some of the links cover integration but many cover using linux *instead* of AD

---

### Post by Monicker on 2008-06-01
> **mohenjo said:**
> What would the Ubuntu version of "Active Directory" be, and where might I go to find some good documentation for setting it up an creating a domain?

I'm not quite sure what you want, but for centralized authentication, the *nix equivalent is NIS.

[http://www.linux-nis.org/]("http://www.linux-nis.org/")

If you want something more than that, please give details.

---

### Post by squirrel_chaser on 2008-06-01
You may want to look at OpenLDAP.  It can provide a central authentication source for users on your network.  Although not Ubuntu specific, check out Fedora Directory Services which I think is a front end for OpenLDAP.

---

### Post by mohenjo on 2008-06-01
Thanks for the replies everyone; looks like it's time for me to do some reading! :)

What I'm trying to do is recreate my Win2k3 domain that I have at work, but using Ubuntu for the servers and workstations in the test lab I've got.  My Win2k3 domain uses AD for all user authentication, and that's what I wanted to replicate in Linux.

I'll give some of these a look over and will hopefully get working on the fun stuff (mail, dhcp, dns, etc)

---

### Post by Yfrwlf on 2008-11-14
> **squirrel_chaser said:**
> You may want to look at OpenLDAP.  It can provide a central authentication source for users on your network.  Although not Ubuntu specific, check out Fedora Directory Services which I think is a front end for OpenLDAP.

Huh, maybe the developers should think about supporting some open source packaging APIs/formats then so regardless of your distro you can easily install their software.

Oh wait, then they couldn't use that to try to encourage you to install Fedora.  Shame.

Looks like nice software though, too bad it's stuck like that.  So unless you know how to use alien or how to compile, you may be stuck editing configuration files and trying to set up openLDAP instead.

There are several systems out there you can use for authentication though.  Kerberos + SAMBA is certainly one method but if you don't need AD integration, definitely might be better off sticking to something else.  If you have the money though, there are several closed source solutions, like [http://en.wikipedia.org/wiki/Open_Enterprise_Server](http://en.wikipedia.org/wiki/Open_Enterprise_Server) and Red Hat has their own workstation management systems and software as well, but of course most all that comes at a price.

---

