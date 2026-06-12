---
title: "[SOLVED] Need advice: remote login authentication"
date: 2008-09-05
forum: Security
---

### Post by engocoka on 2008-09-05
Hi All,

I'm interested in establishing a computing lab for the CS major at my liberal arts college.  I have a fair amount of single system Linux experience, but I am less familiar with system wide administration issues.

I'd like to have a setup where I have 20+ computers that authenticate their logins through a central server.  In other words, a student could log into any of these machines, change his/her password, then walk across the room and log into the new machine with his/her new password.  Somehow the client would get an authentication through the server Windows AD style.

I've done some googling on this and ran across lots of LDAP/AD/Kerberos HOWTOs, but the ones I encountered were geared toward getting Linux to authenticate with Windows servers.  I also ran into PAM stuff, but it's not clear PAM itself is what I'm looking for.

Does anybody have any advice on what sort of configuration I should consider in this case on both the server and client end?  Or, if I'm in the wrong forum, could you point me to the right one?  I would greatly appreciate any help.

---

### Post by puppywhacker on 2008-09-07
hi,

I would recommend going the LDAP approch, Windows AD is basically an ldap server as well. PAM provides pluggable authentication modules. One of those modules is libpam-ldap, when you have it installed on 20+ clients everybody would authenticate against the central ldap server. The package smbldap-tools provides the commands to change the password remotely.

Mind you, setting up the ldap authentication is not so easy. Below are the two articles/howto's that I used.

[ldaptastic]("http://times.usefulinc.com/2005/09/25-ldap")
[OpenLDAPServer]("https://help.ubuntu.com/community/OpenLDAPServer")

---

### Post by HermanAB on 2008-09-07
You need NIS, Novell, or Redhat Directory.

All directory systems are LDAP (X500) based.

---

### Post by engocoka on 2008-09-09
Thank you both for your advice.  It looks like LDAP what I was looking/hoping for.

---

