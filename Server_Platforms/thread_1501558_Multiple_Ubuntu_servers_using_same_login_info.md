---
title: "Multiple Ubuntu servers using same login info?"
date: 2010-06-04
forum: Server Platforms
---

### Post by derdud on 2010-06-04
I'm looking to add a few more Ubuntu servers to my network for various functions, but I want the users' login information to be the same across all of them. Is there a way that I can point login validation to the server I already have in place? These are all running 10.04.

---

### Post by bab1 on 2010-06-04
> **derdud said:**
> I'm looking to add a few more Ubuntu servers to my network for various functions, but I want the users' login information to be the same across all of them. Is there a way that I can point login validation to the server I already have in place? These are all running 10.04.

That's what domain logins are for.  You can use NIS or LDAP to hold user information.  Linux users usually end up with an [**_OpenLADP _**]("https://help.ubuntu.com/9.04/serverguide/C/openldap-server.html").  Although it has been around forever, [**_NIS _**]("https://help.ubuntu.com/community/SettingUpNISHowTo")works well.

---

### Post by derdud on 2010-06-04
> **bab1 said:**
> That's what domain logins are for.  You can use NIS or LDAP to hold user information.  Linux users usually end up with an [**_OpenLADP _**]("https://help.ubuntu.com/9.04/serverguide/C/openldap-server.html").  Although it has been around forever, [**_NIS _**]("https://help.ubuntu.com/community/SettingUpNISHowTo")works well.

Ok cool. I'm very familiar with the Windows implementation of LDAP but I wasn't sure how it worked with Linux. Is there anything that makes one better than the other with LDAP and NIS?

---

### Post by bab1 on 2010-06-04
> **derdud said:**
> Ok cool. I'm very familiar with the Windows implementation of LDAP but I wasn't sure how it worked with Linux. Is there anything that makes one better than the other with LDAP and NIS?

If you understand LDAP then don't even bother with NIS.  NIS is all flat files and not very flexible.

The functionality of AD is not quite duplicated unless you create and integrate all the components yourself.  To come close to AD you will need OpenLADP+Kerbros+BIND9.

There is one interesting project (I have not tried it) is called [**_389 Directory server_**]("http://directory.fedoraproject.org/wiki/Howto:DebianUbuntu").  You can use Kerbros and bind9 with it.  Here is the [**_Kerberos _**]("http://directory.fedoraproject.org/wiki/Howto:Kerberos")information.

This is a major project, not a simple install and add users.  Windows AD and Novell eDirectory are mature stable products and way ahead of the opensource community.

---

### Post by drdos2006 on 2010-06-04
Check out Samba4, it might suit your needs.

Has Active Directory.....

regards

---

### Post by HermanAB on 2010-06-05
There is no shortage of authentication daemons:
Samba
NIS
LDAP
RADIUS
PAM MySQL

These things are just authentication with a database back-end, no biggie.

---

### Post by derdud on 2010-06-07
> **bab1 said:**
> If you understand LDAP then don't even bother with NIS.  NIS is all flat files and not very flexible.

The functionality of AD is not quite duplicated unless you create and integrate all the components yourself.  To come close to AD you will need OpenLADP+Kerbros+BIND9.

There is one interesting project (I have not tried it) is called [**_389 Directory server_**]("http://directory.fedoraproject.org/wiki/Howto:DebianUbuntu").  You can use Kerbros and bind9 with it.  Here is the [**_Kerberos _**]("http://directory.fedoraproject.org/wiki/Howto:Kerberos")information.

This is a major project, not a simple install and add users.  Windows AD and Novell eDirectory are mature stable products and way ahead of the opensource community.

I didn't get very far with OpenLDAP. The documentation you linked me to on Ubuntu's site doesn't seem to be accurate. I got as far as installing slapd and ldap-utils. After that, the documentation says:

> The installation process will prompt you for the LDAP directory admin password and confirmation

This never happened. I wasn't prompted for anything. Even on the next step where I used dpkg-reconfigure on slapd, it never asked me for a DN, password, or anything else. When I try to go through the configuration steps, it asks me for a password (which of course was never set), so it doesn't work.

Am I missing something here?

---

