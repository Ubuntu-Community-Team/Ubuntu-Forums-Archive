---
title: "Ubuntu server 10.04/ samba beginners question"
date: 2010-10-19
forum: Server Platforms
---

### Post by Danyhenriquez on 2010-10-19
Hi all,

I have a question that is probably easy for the most of you, but i installed my |Ubuntu server 10.04 yesterday. 

I 've already gotten quite far but i cannot get samba to work properly.

What i want to do is to create a home file server with the zentyal 2.0 web interface. The google function on my interweb personal computer is not very helpfull at this point.

when i fiddle around with the zentyal options, i am not getting any further. I found the smb.conf file and i was wondering what needs to be changed in order to make the shares available for my entire netwotk without the nee a password or logon?




[global]
 workgroup = WORKGROUP
 netbios name = ubuntu
 server string = Zentyal File Server
 enable privileges = yes
 interfaces = lo,eth0
 bind interfaces only = Yes
 passdb backend = ldapsam:ldapi://%2fvar%2frun%2fslapd%2fldapi
 ldap ssl = Off
 log level = 1
 syslog = 0
 log file = /var/log/samba/%m
 max log size = 50
 vfs objects = full_audit
 full_audit:success = connect opendir open disconnect unlink mkdir rmdir r$
 full_audit:failure = none
 smb ports = 137 138 139 445
 name resolve order = wins bcast hosts
 time server = Yes
 printcap name = CUPS
 wins support = Yes
 dns proxy = Yes
 ldap suffix = dc=ubuntu,dc=localdomain
 ldap machine suffix = ou=Computers
 ldap user suffix =  ou=Users
 ldap group suffix =  ou=Groups
 ldap idmap suffix = ou=Idmap
 ldap admin dn = cn=ebox,dc=ubuntu,dc=localdomain
 map acl inherit = Yes
 printing = cups

 encrypt passwords = Yes
 obey pam restrictions = No
 ldap passwd sync = Yes
 mangling method = hash2

 logon script = logon.bat
 logon drive = H:

^G Get Help ^O WriteOut ^R Read File^Y Prev Page^K Cut Text ^C Cur Pos
^X Exit     ^J Justify  ^W Where Is ^V Next Page^U UnCut Tex^T To Spell

---

### Post by luvshines on 2010-10-19
Looks like you are using LDAP as username/password backend, right ?

I think, you can try adding:```

## Append to global section
[global]
map to guest = bad user

## Append to individual shares [share-name]
guest ok = yes

```

Restart the smbd service after making changes to smb.conf

It seems to be working for me, see if it works for you too

---

### Post by Danyhenriquez on 2010-10-20
Thank you for your reply.

I discovered that if i install the "easy"to use zentyal/ebox modules that zentyal/ebox messes  the smc.conf file up  constantly.

I added "authentication = share" and added guest ok = yes to my share definitions. 

Now it works perfectly.

---

