---
title: "Dalorradius / Freeradius with Active Directory?"
date: 2011-02-16
forum: Server Platforms
---

### Post by sentinelace on 2011-02-16
I have a freeradius server running with daloradius.  This is all working fine, however, it will take me a year to input all our barcode users that I need entered into the users file for freeradius.  How can I export users from AD into this?  I also noticed the freeradius user list is different from where the gui daloradius has their list.  Is there a easier way to configure this?  I would really just like to add users right from the panel that are already in active directory.  What do I need to do?

---

### Post by HermanAB on 2011-02-16
Howdy,

ADS is a regular LDAP database, so you an query the users and groups quite easily, then use a programmer's editor or Perl to reformat the resultant file.

Google for "Windows ADS users query".

Ferinstance: [http://serverfault.com/questions/18018/whats-the-ad-query-syntax-to-enumerate-all-users-for-a-particular-group](http://serverfault.com/questions/18018/whats-the-ad-query-syntax-to-enumerate-all-users-for-a-particular-group)

---

