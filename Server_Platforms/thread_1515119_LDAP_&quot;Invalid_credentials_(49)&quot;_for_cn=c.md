---
title: "LDAP &quot;Invalid credentials (49)&quot; for cn=config (10.04 svr)"
date: 2010-06-21
forum: Server Platforms
---

### Post by brettg on 2010-06-21
OK, so I am experimenting with setting up an LDAP Server using [this guide]("http://tuxnetworks.blogspot.com/2010/06/howto-ldap-server-on-1004-lucid-lynx.html")

Everything went well, I can retreive entries as well as add new entries such as users and groups to my dn without trouble.

For example, if I do this;

```
ldapadd -x -D "cn=admin,dc=example,dc=com" -W -f example.ldif
```

It asks for the admin password which works fine. So far so good.

My problem arises when I try to add or modify the global configs, ie: cn=config

Specifically, I am trying to follow [this guide]("http://doc.ubuntu.com/ubuntu/serverguide/C/samba-ldap.html") to add samba support.

When I get to this step;
```

ldapadd -x -D cn=admin,cn=config -W -f /tmp/cn\=samba.ldif
```

It all goes pear shaped with the error "Invalid Credentials (49)" as mentioned in the subject.

Likewise, it also fails if I try something like this;

```
#ldapadd -x -D cn=admin,cn=config -W -f /etc/ldap/schema/cosine.ldif
Enter LDAP Password: 
ldap_bind: Invalid credentials (49)

```

I have done plenty of googling regarding this but nearly all of the people having similar problems are experiencing them at the point where they are running the first command (updating their org dn which works fine for me).  Also, most of the remaining solutions involve messing with slapd.conf which is depreciated and does not exist on 10.04

Clearly, my admin password works because I can update my dn using it without trouble. I can also login using it via phpLDAPadmin.

Any clues as to where to look for a solution would be greatly appreciated.

Thanks in advance. In the meantime I will keep on trying to fix it myself. Will post solution here if I find it.

Details (sanitized and abridged) follow;

```
#ldapsearch -x
dn: dc=example,dc=com
objectClass: top
objectClass: dcObject
objectClass: organization
o: Example
dc: example
description:: TERBUCBTZXJ2ZXIg

# admin, example.com
dn: cn=admin,dc=example,dc=com
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
```

```
#cat /etc/default/slapd
# Location of the slapd configuration to use.  If using the cn=config          
# backend to store configuration in LDIF, set this variable to the             
# directory containing the cn=config data; otherwise set it to the location    
# of your slapd.conf file.  If empty, use the compiled-in default              
# (/etc/ldap/slapd.d). 
SLAPD_CONF=

```

```
#cat /etc/ldap/slapd.d/cn\=config.ldif 
dn: cn=config
objectClass: olcGlobal
cn: config
olcArgsFile: /var/run/slapd/slapd.args
olcLogLevel: none
olcPidFile: /var/run/slapd/slapd.pid
olcToolThreads: 1
structuralObjectClass: olcGlobal
entryUUID: 7d679c76-1122-102f-8ba5-0f8bc5dfd644
creatorsName: cn=config
createTimestamp: 20100621014601Z
entryCSN: 20100621014601.089636Z#000000#000#000000
modifiersName: cn=config
modifyTimestamp: 20100621014601Z
```

```
/etc/ldap# grep -r RootDN *
slapd.d/cn=config/olcDatabase={1}hdb.ldif:olcRootDN: cn=admin,dc=example,dc=com
```

If there are any other command outputs or relevant config files I can post here please let me know.

---

### Post by brettg on 2010-07-07
Well, I couldn't resolve the actual error as per the subect line of this post but I did manage to figure out how to install LDAP + Samba on a lucid server, which was the main point of the excercise.

I have described the step by step process in a howto post on my blog.

[http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html]("http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html")

---

### Post by dkocuvan on 2010-12-11
Same problem here.

But according to: [http://www.howtoforge.com/install-and-configure-openldap-on-ubuntu-karmic-koala](http://www.howtoforge.com/install-and-configure-openldap-on-ubuntu-karmic-koala)

this helped me out:

```
slappasswd -h {MD5}
```

Type the wanted pasword twice and copy the result in to the text below.

```
vi config.ldif 
```

Content of config.ldif: (modified to avoid missing attribute error)

```

dn: cn=config
changetype: modify

dn: olcDatabase={0}config,cn=config
changetype: modify
add: olcRootDN
olcRootDN: cn=admin,cn=config

dn: olcDatabase={0}config,cn=config
changetype: modify
add: olcRootPW
olcRootPW: {MD5}your password here

dn: olcDatabase={0}config,cn=config
changetype: modify
delete: olcAccess

```

Load the config.ldif into the openldap server:

```
ldapadd -Y EXTERNAL -H ldapi:/// -f config.ldif 
```

From now on openldap can be configured and manipulated as before, but no longer by issuing commands like:
 
```
ldapadd -Y EXTERNAL -H ldapi:// -f file
``` 

but rather:

```
ldapadd -x -Y EXTERNAL -H ldapi:// -D cn=admin,cn=config -W -f file
```

---

### Post by tiger74 on 2012-02-15
Thank you so much!!! :)
I've been spending many sleepless night for this.
Until finally I use the correct keywords on Google to find this posting.

Thankssssss :)
Fajar
[http://linux3.arinet.org](http://linux3.arinet.org)
:popcorn:

---

### Post by florenc on 2012-04-18
HI
I am to  setting up ACL in openldap server but when i use this comand
[B]ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase=hdb olcAccess

show this problem:
 root@ubuntu:/# ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase=hdb olcAccess
Enter LDAP Password: 
ldap_bind: Invalid credentials (49)
root@ubuntu:/# 
password is secret but doesnt accept
any help?
Best regards.

[/B]

---

