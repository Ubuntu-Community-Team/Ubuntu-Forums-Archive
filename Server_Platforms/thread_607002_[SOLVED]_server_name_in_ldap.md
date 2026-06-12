---
title: "[SOLVED] server name in ldap"
date: 2007-11-08
forum: Server Platforms
---

### Post by xyrer on 2007-11-08
Hi, I have been trying to make squid authenticate with ldap but first I need to have a bullet proof working ldap server; now, all the documentation I have seen has this "dc=exmaple,dc=com" form, do I really need to have a .com .net or .whatever? because my server doesn't have a domain, it doesn't need it and it's never gonna have one.

Please, everything I try fails and I don't know what is wrong.

---

### Post by koenn on 2007-11-08
> **xyrer said:**
> Hi, I have been trying to make squid authenticate with ldap but first I need to have a bullet proof working ldap server; now, all the documentation I have seen has this "dc=exmaple,dc=com" form, do I really need to have a .com .net or .whatever? because my server doesn't have a domain, it doesn't need it and it's never gonna have one.

Please, everything I try fails and I don't know what is wrong.

It's how the ldap naming scheme works, just like dns, so you need to have a "fully qualified domain name", yes. 

For private (i.e. not accssible from outside) use, you can make something up.  Microsoft suggests .local domains. iana has some top level domains for private use (..yx  and some others in the x, y and z area)

But have a look in your /etc/hosts file first : chances are your computer already has a fqdn.

---

### Post by xyrer on 2007-11-08
But the hostname of my server doesn't have an extension, do I have to change the hostname? I mean, that would screw up the 87 jabber clients and 200 squid users.

---

### Post by geforce123 on 2007-11-10
Yes you need to have a fqdn, but in fact you don't need it :P

I would suggest you to use a .local or .xyz (ex: yourcorp.local) and use it in LDAP..

Now,
Do you host your own DNS servers ?

Add a zone youcorp.local that would point out to your server (preferably internal/LAN IP), so this host name won't point out somewhere in the internet when it is resolved

---

### Post by xyrer on 2007-11-10
I don't have my own DNS, but I'm planning to due to this problem, by the way, with my own DNS, could I redirect let's say "intranet.mycorp.local" to 192.168.1.1/intranet/ ?

---

### Post by geforce123 on 2007-11-11
yup, but not entirely with the DNS:

- the dns will resolve intranet.mycorp.local to IP 192.168.1.1

- the web server (i.e apache) will receive the requested hostname (intranet.mycorp.local) and display some site of your choice. You can have different web sites for [www.mycorp.local](www.mycorp.local), intranet.mycorp.local and admin.mycorp.local if you want to... It's all in the configs.

---

