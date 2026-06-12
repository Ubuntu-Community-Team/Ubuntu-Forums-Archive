---
title: "Multi-master kerberos server with an openldap backend install script"
date: 2017-08-15
forum: Server Platforms
---

### Post by thseeger on 2017-08-15
Hello,
 
I would like to give the community something back for all the help i found here over the years. I wrote a bash script to install a multi-master kerberos server with an openldap backend. During the run it creates a ca infrastructure, actually a root ca, an intermediate ca and a signing ca. For the replication sasl is used and for the renewing of the needed kerberos tickets a k5start based service is installed. sssd authentication is used as frontend. In addition you can use the setup as backend for dns, autofs, addressbook, owncloud, zarafa, etc. If you want you can use [COLOR=#000080]_[PKINIT]("https://web.mit.edu/kerberos/krb5-1.13/doc/admin/pkinit.html")_[/COLOR] to authenticate.

The script is for playing around with kerberos and openldap. I advice you to use one or more fresh vm for the playground. You can change and tweak your setup and easy reinstall everything. Feel free to use this script at your own charge, I cannot be held responsible for what YOU do on YOUR administered system.

 Actually, I had planned a blog post series, which explains the individual steps and possibilities on some examples, but since we have gotten a daughter and the little one gets the most of my attention, there is little time for this.

  I will update the script from time to time and add new features.  

 If you interested to play around with kerberos and openldap you can find my "installer" script on: [COLOR=#000080]_[https://wp.tntnet.eu/?p=112](https://wp.tntnet.eu/?p=112)_[/COLOR]

  Have fun!

Regards
 
  Thorsten

---

