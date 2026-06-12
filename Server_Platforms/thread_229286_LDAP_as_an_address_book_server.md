---
title: "LDAP as an address book server"
date: 2006-08-04
forum: Server Platforms
---

### Post by fommil on 2006-08-04
I have managed to install slapd and using ldap-account-manager (which required some fiddling to remove Samba modules), I was able to add a group including two users; one with a password and one without. My end goal is to set up an Address book server sharing a single address book, read/writable by 4 people.

However, this is proving very difficult as most online tutorials [e.g. [http://www.onlamp.com/pub/a/onlamp/2003/03/27/ldap_ab.html]](http://www.onlamp.com/pub/a/onlamp/2003/03/27/ldap_ab.html]) use a very different slapd.conf file (e.g. Ubuntu stores the passwords in the database itself).

Does anyone have a HOWTO on how to do this specific task the "Ubuntu way". Ideally, I'd like to see how I go from a Ubuntu box without LDAP installed, to a Ubuntu box with a password-protected Address Book server, sharing the same writable address book to 4 users.

---

