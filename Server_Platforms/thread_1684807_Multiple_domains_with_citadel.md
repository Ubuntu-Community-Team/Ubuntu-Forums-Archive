---
title: "Multiple domains with citadel"
date: 2011-02-09
forum: Server Platforms
---

### Post by jenka on 2011-02-09
Hi!

I've got citadel running fine with one single domain name. But now I want multiple domain names to work. And i dosnt really know how to do.. Cant find any tutorial. So pls anyone? :)

/jenka

---

### Post by volkswagner on 2011-02-09
You can simply use the web interface.

Log into the web interface with an administrative user.  Select the administration tab, choose Domain Names and Internet Mail Config, then add the domains to the list of local host aliases.

Of course will will need the MX records for the DNS server in place for each domain pointing to your Citadel server as with your main mail domain.

---

### Post by jenka on 2011-02-10
> **volkswagner said:**
> You can simply use the web interface.

Log into the web interface with an administrative user.  Select the administration tab, choose Domain Names and Internet Mail Config, then add the domains to the list of local host aliases.

Of course will will need the MX records for the DNS server in place for each domain pointing to your Citadel server as with your main mail domain.

Ok but i cant connect the new domain to an user account. The user can only get the domain name I entered in FGDN.

---

### Post by d.okuboyejo@gmail.com on 2012-08-22
I had the same trouble, but fixed the issue as follows

NOTE:
the domain specified in the Advanced->Edit site-wide configuration->General site configuration items->Fully qualified domain name is the default domain for every user creates, to specify separate domain for each user, follow beneath guide

1) add as many domain you want from Administration->Domain names and Internet mail configuration->Local host aliases
2) create unique user across all of your domain (if user1 is in domain1, then user1 can't be in domain2 also)
3) ensure each user has a valid email (edit user configuration) with one of your preferred domain (created in 1 above)
4) test by sending a mail to one of the 
enjoy

---

