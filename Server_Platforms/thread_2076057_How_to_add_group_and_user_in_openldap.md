---
title: "How to add group and user in openldap ?"
date: 2012-10-25
forum: Server Platforms
---

### Post by honey_bee on 2012-10-25
hi,
I have created two OUs in my ubuntu box. I want to add two groups for example
In sales organizational Unit i want to add group which as name local_sales and has one users with user name "jon".
 
 
[FONT=Courier New][SIZE=3]**dn: ou=Sales,dc=test,dc=local**[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]**ou: Sales**[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]**objectClass: organizationalUnit**[/SIZE][/FONT]
 
[FONT=Courier New][COLOR=black][FONT=Courier New][FONT=Tahoma][SIZE=3]Same thing I want to repeate it with Marketing OU which has a group i.e local_marketing & has a user "smith".[/SIZE][/FONT][/FONT][/COLOR][/FONT]
[FONT=Courier New]
[/FONT]
[FONT=Courier New][SIZE=3]**dn: ou=Marketing,dc=test,dc=local **[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]**ou: Marketing**[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]**objectClass: organizationalUnit**[/SIZE][/FONT]


**[FONT=Courier New]To add group i.e local_sales I write in my following [/FONT]**group.ldif file
 
dn: cn=local_sales ,ou=Sales,dc=test,dc=local
objectclass: groupofsales
cn: local_sales 
description: group of local sales persons
 

**[FONT=Courier New][SIZE=3]To add group i.e local_marketing I use teh following [/SIZE][/FONT]**

dn: cn=local_marketing ,ou=Marketing,dc=lest,dc=local
objectclass: groupofmarketing
cn: local_marketing
description: group of local marketing persons
 

Kindly guide me that is it the correct way way to add the group inside the OU's ? Also let me know how can I add users in these two groups ?
 
thanks
honey.

---

### Post by kennethconn on 2012-10-27
Have you read [https://help.ubuntu.com/12.04/serverguide/openldap-server.html](https://help.ubuntu.com/12.04/serverguide/openldap-server.html)?

You might want to look at something like phpldapadmin.

---

### Post by honey_bee on 2012-10-31
thanks for the reply.Well I want to do all through command line. I just need guidence that how can I  create groups and then add users into the group.Are my steps are correct which I have been posted earlier?
 
thanks,
honey/.

---

### Post by kennethconn on 2012-10-31
I'm not certain but I think the objectclass should be groupOfNames

I find OpenLDAP to be quite confusing, someone else might be in a better position to advise.

---

### Post by honey_bee on 2012-11-01
thanks "kennethconn" for the reply. Well really openldap is quite confusing thing.Hard to understand it. I have google it but found very complex configuration. I just want a very basic configuration.I mean no security should be involve .A simple & plain configuration will leade me to work for more indeapth .
 
At  the moment my basic object is how to populate a openldap Directory with creating group and then adding users in it. In ubuntu forum (Server) still yet i have not found any proper guidence which I have mentioned above is correct or there is need some more improvement in it ?
 
any body kindly guide me ....
 
thanks,
honey.

---

### Post by kennethconn on 2012-11-01
I thought I just did...

Did you read the link I gave you?

> At the moment my basic object is how to populate a openldap Directory with creating group and then adding users in it

That objective is different to your original post (group within a group), so you need to be clear on what it is you require.

I really think you should look at phpldapadmin.

---

