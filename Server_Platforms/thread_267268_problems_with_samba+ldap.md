---
title: "problems with samba+ldap"
date: 2006-09-28
forum: Server Platforms
---

### Post by ledFloyd on 2006-09-28
hi all,
i'm new linux's user...
i'm trying to install samba on ubuntu server 6.06 with OpenLDAP password backend as a Primary Domain Controller.
I follow this howto: [http://www.idealx.com/content/view/184/169/lang,en/](http://www.idealx.com/content/view/184/169/lang,en/)
now i'm stopped when i search the SID:
```
# net getlocalsid
[2006/09/28 17:55:34, 0] lib/smbldap.c:smb_ldap_start_tls(546)
Failed to issue the StartTLS instruction: Connect error
```

i had tried this:
```
# ldapsearch -ZZ
ldap_start_tls: Connect error (-11)
        additional info: error:14077410:SSL routines:SSL23_GET_SERVER_HELLO:sslv3 alert handshake failure
```

can you help me???
bye

p.s. sorry for my english :-D

---

### Post by bluefrog on 2006-09-29
try to get rid of all TLS part for the time being.

When your samba-ldap is working/configured correctly, you will have time to figure out TLS (I have reached the first step not the second yet...)

James

---

### Post by ledFloyd on 2006-09-29
thank you...
i'had set the 'ldapTLS="0"' but nothing...
but i find the problem ( :-) )....there was a problem with passdb backend in smb.conf, i'had commented it and now i get the SID with # net getlocalsid.
But now i have another problem... :( 

> # smbldap-populate
Populating LDAP directory for domain LEDFLOYD (S-1-5-21-2974539202-2716486170-801334603)
(using builtin directory structure)

adding new entry: dc=led,dc=floyd
failed to add entry: Can't contact LDAP server at /usr/sbin/smbldap-populate line 495, <GEN1> line 2.
adding new entry: ou=Users,dc=led,dc=floyd
failed to add entry: Can't contact LDAP server at /usr/sbin/smbldap-populate line 495, <GEN1> line 3.
adding new entry: ou=Groups,dc=led,dc=floyd
...
[cut]
...

Please provide a password for the domain root:
Can't contact LDAP server at /usr/share/perl5/smbldap_tools.pm line 353.

i don't know what is the problem...i'm searching on google but without many results.
thank for your help
bye

---

### Post by bluefrog on 2006-09-29
will post you complete samba ldap procedure in 2 or 3 hours when I get back from work

meanwhile your problem has certainly something to do with /smbldap/smbldap.conf and smbldap_bind.conf (can't remember exact names and location right now)

you also have to tweak:

/etc/ldap.secret
/etc/ldap/ldap.conf

James

---

### Post by ledFloyd on 2006-09-29
hi,
sorry for delay.....but i'had visited only now the forum...!
i've created archive with all my conf file(i hope :-) )

[http://rapidshare.de/files/34887506/sambaConfFile.tar.html](http://rapidshare.de/files/34887506/sambaConfFile.tar.html)

please remember me if i had forget something....
thank you

bye

---

### Post by bluefrog on 2006-09-29
Read a bit more smbldap config. I think passwords have to be clear text in smbldap_bind.conf (that's why you chmod 400 this file)

I am sorry I have no time to do more this weekend.

james

---

### Post by ledFloyd on 2006-09-30
ok...

---

