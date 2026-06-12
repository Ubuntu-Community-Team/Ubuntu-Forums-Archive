---
title: "Question on openLDAP, why need DNS server?"
date: 2008-02-11
forum: Server Platforms
---

### Post by cpthk on 2008-02-11
I try to follow the tutorial here:
[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

But I don't understand is why do we need a DNS server on step17. Aren't windows clients are in company internal network? Why not just give it a ip address?

---

### Post by crouton on 2008-02-14
I'm not an expert on the subject, but I believe that DNS is how LDAP can keep track of computers/objects on the network.  

[This link on Active Directory and DNS]("http://www.informit.com/articles/article.aspx?p=26896") is good related reading because Active Directory is Microsoft's interpretation of LDAP with some bells and whistles added on.  It would appear that for similar reasons, vanilla LDAP and DNS should go hand in hand.

---

### Post by cpthk on 2008-02-14
So does my company has to purchase a domain name in order to set up a LDAP server?

---

### Post by astrotech226 on 2008-02-14
> **cpthk said:**
> 
But I don't understand is why do we need a DNS server on step17. Aren't windows clients are in company internal network? Why not just give it a ip address?

You don't need a DNS server for LDAP to work.  And you also don't actually need a domain name to make it work either.  What you are referring to is more of the "container" for the LDAP database.  I think this is called the "suffix" in the slapd.conf file.

If you have a company called "xyzwidgets", it would be common to create a suffix of:

```
dc=xyzwidgets,dc=com
```

You can use LDAP to store all sorts of data.  I use it to store my Samba database, radius information as well as corporate address books and a few other things.  In Samba, users are referred to as "People".  So those people might be found in the LDAP database as:

```
ou=People,dc=xyzwidgets,dc=com
```

Where "ou" means Organizational Unit.  What do you want to use LDAP for?

---

### Post by crouton on 2008-02-15
> **cpthk said:**
> So does my company has to purchase a domain name in order to set up a LDAP server?

Nope, you can use a non-addressable domain like abc.local.

---

### Post by Brazen on 2008-02-15
LDAP does not need a DNS server, but a Windows Domain (implemented by a Samba or Windows Domain Controller) does need a DNS server.

As Crouton said, for internal user only, you do not need to purchase a domain name, just use something.local.

---

### Post by cpthk on 2008-02-16
> **Brazen said:**
> LDAP does not need a DNS server, but a Windows Domain (implemented by a Samba or Windows Domain Controller) does need a DNS server.

As Crouton said, for internal user only, you do not need to purchase a domain name, just use something.local.

Thanks for reply. Windows Domain does need a DNS server? Really? In which part? Because I actually have a samba server in my house, and I do not have a DNS server. But all my other computers are able to log in to samba using NETBIOS Domain Name. For example, at the domain field I simply type in the samba server's NETBIOS name. Why?

---

### Post by Brazen on 2008-02-16
> **cpthk said:**
> Thanks for reply. Windows Domain does need a DNS server? Really? In which part? Because I actually have a samba server in my house, and I do not have a DNS server. But all my other computers are able to log in to samba using NETBIOS Domain Name. For example, at the domain field I simply type in the samba server's NETBIOS name. Why?

Well, granted, I was basing this on a Windows 2000 domain and now that I think of it, of course Samba is based on the old Window NT domain protocols which indeed did not require DNS (in fact Microsoft was pushing there own WINS over the standard DNS).

So, I admit it, now that I think about it, I was wrong in that regard to Samba (I have set up several Win2k and Win2k3 domains though, and I assure they will not even allow you to complete the installation without specifying a DNS server or allow the wizard to install one locally).

My _guess_ is that you can get around having a DNS server by usring Samba's built-in WINS implementation instead.  The only difference between your home domain and a domain with LDAP should be some authentication settins in Samba.  However, a Windows NT domain did not use LDAP, so you are getting Windows-2000-domain-like when you add in LDAP.  While LDAP does not need a DNS server, the way Samba stores account information when it is in "LDAP mode" may require queries that depend on a DNS server.

So the short, revised answer is, OpenLDAP does not need DNS and Samba does not need DNS, but using Samba with LDAP may require DNS.  Or you may be able to get around it.

However, if the network you are setting this up for would actually benefit from using LDAP, then I would almost guarantee they will also benefit from using DNS over NetBios.

---

### Post by Brazen on 2008-02-16
This from Wikipedia may shed some light:

"Since an LDAP server can return referrals to other servers for requests the server itself will not/can not serve, a naming structure for LDAP entries is needed so one can find a server holding a given DN. Since such a structure already exists in the Domain name system (DNS), servers' top level names often mimic DNS names."

From this it makes sense why Samba is probably hard-coded to use a DNS structure to create the LDAP schema.

---

