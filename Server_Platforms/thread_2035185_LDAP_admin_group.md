---
title: "LDAP admin group"
date: 2012-07-30
forum: Server Platforms
---

### Post by sCHween on 2012-07-30
Hi all

i just tried to configure an LDAP to manage our logins within a dmz. So far everything worked fine expect to add a group which has admin privileges.

See here the configuration of the olcAccess objects:
```
sCHween@asterix:~$ sudo ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase=hdb olcAccess
dn: olcDatabase={1}hdb,cn=config
olcAccess: {0}to attrs=userPassword,shadowLastChange 
by self write 
by anonymous auth 
by dn="cn=admin,dc=dmz,dc=to" write 
by dn="cn=Administrators,ou=groups,dc=dmz,dc=to" write 
by * none

olcAccess: {1}to dn="dc=dmz,dc=to" 
by dn="cn=admin,dc=dmz,dc=to" write 
by dn="cn=Administrators,ou=groups,dc=dmz,dc=to" write 
by self write 
by * read

olcAccess: {2}to dn.sub="ou=groups,dc=dmz,dc=to" 
by dn="cn=admin,dc=soreco, dc=vn" write 
by dn="cn=Administrators,ou=groups,dc=dmz,dc=to" write 
by self write 
by * read

olcAccess: {3}to dn.sub="ou=people,dc=example,dc=com" 
by dn="cn=admin,dc=dmz,dc=to" write 
by dn="cn=Administrators,ou=groups,dc=dmz,dc=to" write 
by self write 
by * read

olcAccess: {4}to dn.sub="ou=groups,dc=example,dc=com" 
by dn="cn=admin,dc=dmz,dc=to" write 
by dn="cn=Administrators,ou=groups,dc=dmz,dc=to" write 
by self write 
by * read

olcAccess: {5}to attrs=loginShell,gecos 
by dn="cn=admin,dc=dmz,dc=to" write
by dn="cn=Administrators,ou=groups,dc=dmz,dc=to" write 
by self write 
by * read

olcAccess: {6}to dn.base="" 
by * read

olcAccess: {7}to * 
by self write 
by dn="cn=admin,dc=dmz,dc=to" write 
by dn="cn=Administrators,ou=groups,dc=dmz,dc=to" write 
by * read
```

Hope someone could help me out to get this things working.
Thanks in advance - best regards, sCHween

---

### Post by sCHween on 2012-08-06
nobody with an idea to support me?

---

### Post by kennethconn on 2012-08-06
What command(s) did you use to do this and how exactly did it work or not work?
 
You also say it is worked as expected until except to add an admin group. What does that mean?
 
The more detail you provide, the better chance people will be able to help you out.

---

### Post by sCHween on 2012-08-07
Sorry to be imprecise - i will try again.
What I want to achieve:

"cn=Administrators,ou=groups,dc=dmz,dc=to" is a group which I could assign to some LDAP users and the could manage the LDAP.

So I thought i could give this group the same rights as "cn=admin,dc=dmz,dc=to" and it should work.

So i checked all my entries for the olcAccess - because in my understanding, the manage the security.
The structure looks okay for me and i tested with a user which was assigned to the Administrators group. I can login and everything but I was unable to edit some other users or groups.

Hope you understand now what i wanted to discuss :)
The easiest question I could ask is:
How can i add a group which have the full management rights?

Thanks in advance - best regards, sCHween

---

### Post by kennethconn on 2012-08-08
I get what you would like to achieve, it is the details of what you have done so far that I was asking for, specifically:
 
What command(s) did you use to add the Administrators group?
What command(s) did you use to add a user to this Administrators group?
 
Stick with it.

---

