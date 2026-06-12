---
title: "For newbies with Linux, is it better LDAP or Kerberos?"
date: 2009-10-24
forum: Server Platforms
---

### Post by frenchn00b on 2009-10-24
Advantages are: 

If you NFS export /home on a large, protected machine to the local network, then use LDAP on that machine to decide who logs in, then all the machines **on the local net become special. It's like every user has an account on all machines...and all their data is always there.**

what is better to use NIS/Kerberos or LDAP, for newbies?

---

### Post by scorp123 on 2009-10-25
Was that a question ??

---

### Post by frenchn00b on 2009-10-26
> **scorp123 said:**
> Was that a question ??

My goal is to have a server for the password and users, but unfortunately this is extremely complicate thing. 

The situation is that I choosed LDAP because it was written that it was less complicated to do. but still. i cant

Hello
I mean this is is not working
[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

first squeeze change the dc-examples lines with the name of my router. 

second, this operation is not standard:
```
Now, add your entries to the LDAP:

    *

      stop LDAP daemon: sudo /etc/init.d/slapd stop
    *

      delete the content that was automatically added at installation: sudo rm -rf /var/lib/ldap/*
    *

      add the new content sudo slapadd -l init.ldif 
    *

      correct permissions on the database sudo chown -R openldap:openldap /var/lib/ldap
    *

      start LDAP daemon: sudo /etc/init.d/slapd start
```

there shoudl be some tools to add users normally without changing that much the config

for the moment, what i did was: 
adding the password to the slapd.conf
 and the restart of slapd works, luckily 
and there is already error

 

whatever I do I have : ```

ldap_bind: Invalid credentials (49)
```

 no results?
 

Try:
man ldap 
nothing.
wow super, great. 

 ```
ldapmodify -a -D "cn=Directory Manager,dc=example,dc=com" -w password -h server1 -f new.ldif

```

OK, how to add an user, now, using ldapmodify?
how that SSH/ /home are already using, on the server, this LDAP system? In /etc/password, those 1001, 1002, ... i.e. users id's are they the same as the LDAP? Nowhere it is written.

Please give a config on the server /etc/exports file?

Please give on the clients the /etc/fstab to use?
and what to install to make it /home the same as the server

[B]
Could someone program a single script:

installer-LDAP.sh  client 
or 
installer-LDAP.sh server

and in the menu, one can select add client, restart, ... with menu dialog
Why no-one does those simple things, I mean, or it should be coder, or man maker, or we can fund a dpkg-configure thing[/B]

---

### Post by tenmoi on 2009-10-28
what you want is either 389 directory server or zivios.

If you want to go the hard way - this will pay very well anyway - read some books on ldap, kerberos, PAM and you are ready to admin some ldap server.

---

