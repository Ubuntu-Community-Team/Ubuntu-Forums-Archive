---
title: "Problem at OpenLDAP reconfiguration"
date: 2010-05-12
forum: Server Platforms
---

### Post by henriquelm on 2010-05-12
Hello there guys, I have been trying to set up openldap on ubuntu server 9.10 and 10.04 32bits, but right after I type the command "sudo dpkg-reconfigure slapd" I believe I was supposed to go through the following options:

Omit OpenLDAP server configuration? ... No
DNS domain name: ... debuntu.local
Name of your organization: ... Whatever & Co
Admin Password: XXXXX
Confirm Password: XXXXX
OK
BDB
Do you want your database to be removed when slapd is purged? ... No
Move old database? ... Yes
Allow LDAPv2 Protocol? ... No

but instead the reconfiguration skips a few steps and jump from the very first step to where it asks me about the database, so I don't get the chance to set up the organization name and admin password.

Is it a bug? How can I overcome this problem?

---

### Post by henriquelm on 2010-05-13
I guess this explains it all:

[http://ubuntuforums.org/showthread.php?t=1313472]("http://ubuntuforums.org/showthread.php?t=1313472")

---

