---
title: "install slapd using bdb instead of hdb"
date: 2011-10-14
forum: Server Platforms
---

### Post by SwitchLink on 2011-10-14
When using the apt-get install slapd command, the database is configured using the hdb backend.  Can this be changed to bdb?

---

### Post by SwitchLink on 2011-10-17
I have no idea if this is correct, but I thought I'd share what I did.

I stopped slapd.
I directly edited the slapd.d config ldif files located at:  **/etc/ldap/slapd.d**

There were a series of LDIF files that looked very similar to the old slapd.conf file.  I used the [http://www.openldap.org/doc/admin24/index.html]("http://www.openldap.org/doc/admin24/index.html") to get the correct settings.

Once my edits were completed I deleted the database files located at **/var/lib/ldap/** and ran **slaptest -u** to verify all the settings were correct.  Found some typos I had made and fixed those.  Once everything checked clean, I performed 2 commands:

[B]slapadd -l thedatabase.ldif -q
slapindex[/B]

Everything seems to be in order, except requests to the server return more than the supposed default of 500 entries, which causes JXplorer to hang when browsing.

I think that is because I am logged in as the rootDN:  [http://www.openldap.org/doc/admin24/limits.html]("http://www.openldap.org/doc/admin24/limits.html")  but I am still working out the details.

I am only sharing this information because I'm not getting any responses on my ldap questions here, so hopefully I am correct in what I have found so far and that it will help someone else if they find themselves in my position of "some guy built an LDAP server for us, and you need to get this working..."

---

