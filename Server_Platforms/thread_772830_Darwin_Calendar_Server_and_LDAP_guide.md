---
title: "Darwin Calendar Server and LDAP guide?"
date: 2008-04-28
forum: Server Platforms
---

### Post by Apfelmaennchen on 2008-04-28
Hi everyone!

Has anyone tried to set up LDAP as directory service for DCS yet or found any helpful documentation on that topic?

I'd like to set this thing up since it seems very promising in terms of ease of administration. However, I'm very new to LDAP in general and so I'm completely unsure on how to set up the directory so that DCS can bind to it.

Any help is highly appreciated.

Thanks in advance,

A

---

### Post by sharth on 2008-04-29
Currently, Darwin Calendar Server does not support LDAP. It supports Active Directory, which is the OS X version of that. 

See: [http://trac.calendarserver.org/projects/calendarserver/ticket/260](http://trac.calendarserver.org/projects/calendarserver/ticket/260)

Also, Debian has been preparing a NSS backend for the directory. That would allow you to use any service that PAM supports. It's not completely written though.

---

### Post by Apfelmaennchen on 2008-04-30
Ah okay...

Then I was misconceiving things:
I understood it in the way that Active Directory in fact just is an LDAP implementation.

Thanks for pointing that out!

A

---

### Post by brocky102 on 2008-04-30
Active Directory is Microsoft Windows implementation of LDAP. You can join Window and Ubuntu clients to either AD or OpenLDAP both work fine.

This [http://howtoforge.com/openldap-samba-domain-controller-ubuntu7.10]("http://howtoforge.com/openldap-samba-domain-controller-ubuntu7.10") walks you through how to setup a Ubuntu domain controller and how to join Windows clients to it. To join Ubuntu clients to the domain either follow [http://ubuntuforums.org/archive/index.php/t-5409.html]("http://ubuntuforums.org/archive/index.php/t-5409.html") or if you have HardyHeron use:

**sudo apt-get install likewise-open likewise-open-gui krb5-config krb5-user**

I haven't had anything to do with Darwin Calendar Service, but i hope this helps some how

---

### Post by mtuckerb on 2008-12-03
Actually, Darwin Calendar Server does support openldap. It requires some hoop jumping, and a special schema, but I have done it.

---

### Post by s_groening on 2008-12-09
On succeeding using the LDAP backend with Calendarserver, did you manage to get Kerberos working or does it in fact only work with pwauth?

---

### Post by freerkkalsbeek on 2009-02-19
I'm looking for the same, do you have info available on how to set things up?

Would be great if there was a wiki page for it.

Regards,
Freerk

---

### Post by Anders Kvist on 2009-11-05
> **mtuckerb said:**
> Actually, Darwin Calendar Server does support openldap. It requires some hoop jumping, and a special schema, but I have done it.

Couldn't you explain what you did to make it work and maybe even make a guide to get DCS and OpenLDAP up and running together. Would be greatly appreciated :)

/Anders

---

