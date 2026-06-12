---
title: "change password ldap user"
date: 2011-04-13
forum: Server Platforms
---

### Post by gettons on 2011-04-13
Hi all,


I have a problem with my ubuntu workstation.
I am trying to change my ldap user password through passwd command.
When I first create the user on ldap server, I use md5 and create the user password.

This is the entry:

```

dn: uid=boo,ou=People,dc=linux,dc=gettolandia,dc=org
uid: boo
cn: boo
objectclass: posixAccount
objectclass: inetOrgPerson
objectclass: shadowAccount
shadowMax: 999999
shadowWarning: 7
shadowLastChange: 10877
userPassword: {MD5}IKrpa9u8/J9z3VryD0DzEQ==
loginShell: /bin/bash
uidNumber: 9001
gidNumber: 9001
homeDirectory: /home/boo
gecos: boo
displayName: boo
mail: boo@boo.boo
givenName: boo
sn: boo

```

I have installed all the necessary packages on my maverick 32bit desktop.
When I first try to change the password by doing the following I get prompted the current password and all goes well for setting up a new one.

```

boo@gettons-desktop:~$ passwd

```

But If I do that again, It does not recognize my actual password for some reasons.
Infact I get:

```

boo@gettons-desktop:~$ passwd 
Enter login(LDAP) password: 
LDAP Password incorrect: try again
Enter login(LDAP) password: 
Password change aborted
passwd: User not known to the underlying authentication module
passwd: password unchanged

```


Doing that with root user all goes well, I presume because It does not check the actual password while setting the new one up.


Interesting config files on the client:

```

boo@gettons-desktop:~$ cat /etc/pam.d/common-password

password        sufficient      pam_ldap.so
password        required        pam_unix.so nullok obscure min=4 max=8 md5


boo@gettons-desktop:~$ cat /etc/login.defs
...
ENCRYPT_METHOD MD5
...

```



Thanks in advance.

---

