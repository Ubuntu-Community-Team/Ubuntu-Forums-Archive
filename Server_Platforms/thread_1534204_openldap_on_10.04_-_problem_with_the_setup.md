---
title: "openldap on 10.04 - problem with the setup"
date: 2010-07-19
forum: Server Platforms
---

### Post by saphear on 2010-07-19
hello all,
I'm trying to set up a ldap server for a global address book for zarafa. 
I have a fresh ubuntu-server 10.04 (32bit) install and I followed this howto: [https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)
I installed slapd and ldap-utils, I added the three schemas cosine.ldif, nis.ldif and inetorgperson.ldif.
Then I modified the backend.example.com.ldif and replaced all "example" entries with "ubuntusrv" (which is my hostname) and "com" with "local".
I changed the rootpw and added the backend.ubuntusrv.local.ldif. I basically did the same with the frontend.ubuntusrv.local.ldif (replacing all "example" and "com" with "ubuntusrv" and "local"; I didn't touch the mail entry of the test user John Doe.

When I try adding the frontend.ldif it asks me for the password, I enter it and I get some terminal output that several things (group, person etc) were added successfully. But when I try to search for John using "ldapsearch -xLLL -b "dc=ubuntusrv,dc=local" uid=john sn givenName cn" I don't get any results..."no such object (32)".

What am I doing wrong? I'm stuck with the ldap server since a few days now and can't really get it working...

---

### Post by druhboruch on 2010-07-19
This how to is working.
[http://www.opinsys.fi/setting-up-openldap-on-ubuntu-10-04-alpha2](http://www.opinsys.fi/setting-up-openldap-on-ubuntu-10-04-alpha2)

---

