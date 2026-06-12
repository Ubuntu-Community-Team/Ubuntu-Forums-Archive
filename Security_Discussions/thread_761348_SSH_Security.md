---
title: "SSH Security"
date: 2008-04-21
forum: Security Discussions
---

### Post by Drezard on 2008-04-21
I'm running an OpenSSH server on an Ubuntu Server 7.10. What are some quick ways I can secure it? 

Its currently running a default installation state.

Daniel

---

### Post by txapelgorri on 2008-04-21
Hi there:

A good one is to enable Key auth and disable Password auth.

Cheers, Ibon.

---

### Post by lintoolman on 2008-04-21
A couple of things come to mind:

Create a group for ssh users and use only allow users in those groups to ssh in.  This is set in the sshd_config file, "AllowGroups" I think.

Install and configure the program "DenyHosts."  This can be installed with aptitude or apt-get.  I'd recommend reading and understanding what it does before installing on a machine you don't have physical access to.  I especially recommend this program on external facing machines.

And what has already been stated, use keys and turn off password authentication.  But be careful when setting up keys on remote machines you don't have physical access to.  I've been known to lock myself out.  I test the key's and only disable password authentication after I know the keys work.

---

### Post by Dr Small on 2008-04-21
This guide here recommends some server settings:
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

And here is another page:
[http://www.debian-administration.org/articles/87](http://www.debian-administration.org/articles/87)

Dr Small

---

### Post by FakeOutdoorsman on 2008-04-21
Here are some good ones:
[Securing Debian Manual: Securing ssh]("http://www.debian.org/doc/manuals/securing-debian-howto/ch-sec-services.en.html#s5.1")
[Securing OpenSSH]("http://wiki.centos.org/HowTos/Network/SecuringSSH")

---

### Post by HermanAB on 2008-04-21
SSH is secure.  As a minimum, to avoid compromising it, ensure that all passwords on the system are longer than 8 characters.  If you are worried about script kiddies, change the port to a non-standard port and enable a rate limiting filer with iptables.  Denyhosts is not a good idea, since you can inadvertently lock yourself out.  Rate limiting is better and provides protection against all DOS attacks on any service, not just this one service.

---

### Post by DBrocks on 2008-04-21
In /etc/ssshd/sshd.conf, change the port. This will minimize the number of nooby script kiddies, who just scan on port 22, the default SSH port.

---

### Post by Oldsoldier2003 on 2008-04-21
> **HermanAB said:**
> SSH is secure.  As a minimum, to avoid compromising it, ensure that all passwords on the system are longer than 8 characters.  If you are worried about script kiddies, change the port to a non-standard port and enable a rate limiting filer with iptables.  Denyhosts is not a good idea, since you can inadvertently lock yourself out.  Rate limiting is better and provides protection against all DOS attacks on any service, not just this one service.

You can override DenyHosts with an entry in your /etc/hosts.allow but I suppose this in itself isn't that useful unless you are connecting from the private ip or if you have a static ip. Of course if you use public key authentication DenyHosts won't lock you out...

---

### Post by brian_p on 2008-04-21
> **Drezard said:**
> I'm running an OpenSSH server on an Ubuntu Server 7.10. What are some quick ways I can secure it? 

Its currently running a default installation state.

With a strong password the default configuration is secure but many people use ssh keys. This can guard against a weak password being chosen but you have to be careful to look after the passphrase which is chosen to go with it.

Script kiddies are no problem. They are useless and their automatic scripts are hardly up to guessing a user name never mind a strong password. Moving sshd from port 22 to a higher port brings no security benefit.

---

### Post by kevdog on 2008-04-21
> enable a rate limiting filer with iptables

Can you expound on this?  I think you mentioned it another post of mine, but a link or a greater explanation would be most beneficial.

---

### Post by FakeOutdoorsman on 2008-04-22
[Using iptables to rate-limit incoming connections]("http://www.debian-administration.org/articles/187")

---

