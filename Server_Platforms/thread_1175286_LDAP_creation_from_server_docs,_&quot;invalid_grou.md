---
title: "LDAP creation from server docs, &quot;invalid group: 'ssl-cert'&quot;"
date: 2009-06-01
forum: Server Platforms
---

### Post by poke4christ on 2009-06-01
I'm following the instructions for adding LDAP to my server and I've just got Certificates running.  I was trying to go through the process of securing it, but I get the error:

```
zach@UbuntuServer:~$ sudo adduser openldap ssl-cert
adduser: The group `ssl-cert' does not exist.

```

After looking around, it seems that "ssl-cert" is a package that can be added and I'm guessing it creates a group of the same name.  However, no-where in the docs does it say to add this package or do anything with it.  Did I miss something somewhere.  Is this an error in the documentation?

---

### Post by poke4christ on 2009-06-01
Did I post this in the right forum?  If I didn't, where should I have?

---

### Post by FalconV on 2009-07-28
I'm getting this same error as well, I've been googling last night and today and still haven't found any answer, or even anything to show someone else experiencing this other than myself until I found this post.

I've purged slapd and ldap-utils and tried again with the same results.  I'm going through the SSL Cert section again to make sure I didn't miss anything in there instructing to make the ssl-cert group.

---

### Post by etki on 2010-07-29
ssl-cert group is not in minimal server instalation for virtuall appliance try
sudo apt-get install ssl-cert
this package is wraper for openssl and automaticaly create group ssl-cert

---

### Post by alleskapot on 2011-05-18
> **etki said:**
> ssl-cert group is not in minimal server instalation for virtuall appliance try
sudo apt-get install ssl-cert
this package is wraper for openssl and automaticaly create group ssl-cert



Thank you etki! 

root@ubuntu:/etc/ldap/schema# sudo adduser openldap ssl-cert
Adding user `openldap' to group `ssl-cert' ...
Adding user openldap to group ssl-cert
Done.

---

### Post by kuhnza on 2011-10-08
Just what I was looking for. Thanks!

---

