---
title: "Ldap Problems"
date: 2008-11-16
forum: Server Platforms
---

### Post by djh82uk on 2008-11-16
Hi All

I am trying to setup an Ldap server so that my windows machines can connect to a domain and have shared drives etc

What else is it capable of? Login Scripts? bookmarks? address book?

Anyway I followed this tutorial ([http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)) and i first hit a problem when I had to edit slapd.conf, in that there isn't one, but there is a lapd.conf but it is empty eventhough I ran the dpkg configure and chose "no" to omit settings.

I used the tutorials slapd.conf, editied it to my domain and pasted it into ldap.conf

but now when I run sudo smbldap-populate -u 30000 -g 30000 

I get 


adding new entry: cn=Replicators,ou=Groups,dc=chimera,dc=local
failed to add entry: objectClass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 499, <GEN1> line 228.
adding new entry: sambaDomainName=chimera,dc=chimera,dc=local
failed to add entry: invalid DN at /usr/sbin/smbldap-populate line 499, <GEN1> line 236.

Please provide a password for the domain root:
Only root can specify username


Any ideas?

Thanks im using ubuntu 8.10

DJH

---

### Post by djh82uk on 2008-11-16
hmm now it says 


Please provide a password for the domain root:
/usr/sbin/smbldap-passwd: user root doesn't exist


instead

---

### Post by djh82uk on 2008-11-16
anyone?

---

### Post by djh82uk on 2008-11-18
Please can someone help with this, i have reinstalled everything went through it all agian with the same problem

I tried compiling it and still no luck

---

