---
title: "OpenLdap Installed and configured but dont know how to make use of it."
date: 2011-11-13
forum: Server Platforms
---

### Post by mannutheman on 2011-11-13
Hello I'm Manish from New Delhi
I have installed ubuntu server 11.04 in vmware. I have two user "root" and "manish" having same password 123456. 

I have install and configured OpenLDAP in ubuntu server 11.04, (apt-get install slapd openldap-utils)
I entered some entries as followed by tutorials on internet... 

I'm getting the search result using following command:-
ldapsearch -W -D cn=admin,dc=tamkor,dc=net -b dc=tamkor,dc=net

Result:-
# extended LDIF
#
# LDAPv3
# base <dc=tamkor,dc=net> with scope subtree
# filter: (objectclass=*)
# requesting: ALL
#

# tamkor.net
dn: dc=tamkor,dc=net
objectClass: top
objectClass: dcObject
objectClass: organization
o: tamkor.net
dc: tamkor

# admin, tamkor.net
dn: cn=admin,dc=tamkor,dc=net
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword:: e1NTSEF9SklrMmVmeHlDczVZUDRxZnp4Uk13NW9uV25mVld6WUs=

# people, tamkor.net
dn: ou=people,dc=tamkor,dc=net
objectClass: organizationalUnit
ou: people

# groups, tamkor.net
dn: ou=groups,dc=tamkor,dc=net
objectClass: organizationalUnit
ou: groups
 
# rahul, people, tamkor.net
dn: uid=rahul,ou=people,dc=tamkor,dc=net
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
uid: rahul
sn: Sharma
givenName: Rahul
cn: Rahul Sharma
displayName: Rahul Sharma
uidNumber: 2000
gidNumber: 2000
userPassword:: MTIzNDU2Nzg=
gecos: Rahul Sharma
loginShell: /bin/bash
homeDirectory: /home/rahul
shadowExpire: -1
shadowFlag: 0
shadowWarning: 7
shadowMin: 8
shadowMax: 999999
shadowLastChange: 10877
mail: [EMAIL="rahul@tamkor.net"]rahul@tamkor.net[/EMAIL]
mobile: 9999999999
title: System User
initials: RS

# hackers, groups, tamkor.net
dn: cn=hackers,ou=groups,dc=tamkor,dc=net
objectClass: posixGroup
cn: hackers
gidNumber: 2000

# search result
search: 2
result: 0 Success

# numResponses: 7
# numEntries: 6

I added a user named Rahul Sharma with a password as 12345678
Now I have some questions regarding to used this ldap server in real world applications 

 1.  How I configure this openldap server so that I can retrive entries in  windows address book. please direct how to configure addressbook as  well. 

 2. In above configuration i have created a person  entry as Rahul Sharma, so is it neccesory to have a local user account  of Rahul Sharma in ubuntu in order to login through ssh to this ubuntu  server using ldap authentication?...Means is it neccesory that we should  have same account of ldap person in our ubuntu linux.?

3.  I know that a uidNumber should be unique for every entry but what about the gid number?
4. I want to configure samba authentications with this openldap server. please instruct the best way to do it.
Thank you.

---

### Post by luvshines on 2011-11-15
Hi Manish. Nice to hear from ppl @ Delhi :D

> 1. How I configure this openldap server so that I can retrive entries in windows address book. please direct how to configure addressbook as well.
Sorry, I have no experience with this

> 2. In above configuration i have created a person entry as Rahul Sharma, so is it neccesory to have a local user account of Rahul Sharma in ubuntu in order to login through ssh to this ubuntu server using ldap authentication?...Means is it neccesory that we should have same account of ldap person in our ubuntu linux.? With the proper configuration for ssh authentication and LDAP user info fetching, you won't require any local account with the same name on your Ubuntu box

> 3. I know that a uidNumber should be unique for every entry but what about the gid number?
If you are referring to different users having same gidNumber as their primary group, then that is quite possible.
However, if you are referring to different groups having same gidNumber, then that is not a good idea.
I don't LDAP by itself will stop you from creating multiple entries for Users with same uidNumber of multiple entries for Groups having same gidNumber. But only the one which is found first will be honored by the system

> 4. I want to configure samba authentications with this openldap server. please instruct the best way to do it.
I think Samba documentation provided at their official website should be good point to start.

---

### Post by jaal on 2011-11-20
you can follow this page

[http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html](http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html)

---

