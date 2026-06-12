---
title: "openldap: Insufficient access"
date: 2014-11-01
forum: Server Platforms
---

### Post by peridian on 2014-11-01
Hi,

It's been a while since I last touched openldap, and I seem to be struggling with the new olc/ldif alternative to slapd.conf.  (Below is all done on localhost)

I installed slapd, configured the rootDN and rootPW through the dpkg-reconfigure wizard.  I checked the configuration of /etc/ldap/ldap.conf, as well as the ports listened to in netstat.

I have successfully used the below to retrieve the contents of the database:

```
sudo ldapsearch -D "cn=admin,dc=mydomain,dc=com" -W -s sub -x "(objectclass=*)"
```

However, when I try to use my own ldif file to modify the db indexes, I get Insufficient access errors.  At first, I thought perhaps my ldif file was wrong.

So I then tried a simple schema import, with the below command:

```
sudo ldapadd -x -D "cn=admin,dc=mydomain,dc=com" -W -f /etc/ldap/schema/inetorgperson.ldif
```

However, I get the same message, Insufficient access.  I have the admin credentials correct, and I checked with slapcat -n0 that it is set as the rootDN.

So why is the admin account not permitted to modify the database?

Regards,
Rob.

---

### Post by peridian on 2014-11-02
Solved, thanks to this blog: [http://idmoim.blogspot.co.uk/2014/05/ldapadd-insufficient-access-50-openldap.html](http://idmoim.blogspot.co.uk/2014/05/ldapadd-insufficient-access-50-openldap.html)

Adding olcRootDN and olcRootPW to the olcDatabase={0}config.ldif file, and then changing the -D paramater to match that olcRootDN worked.

It seems unbelievably stoopid to me that openldap configuration doesn't set itself up in a manner that you can then work with it.  Makes me think something went wrong during install, or there's a step missing from most tutorials.

Regards,
Rob.

---

