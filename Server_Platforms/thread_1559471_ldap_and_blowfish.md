---
title: "ldap and blowfish"
date: 2010-08-23
forum: Server Platforms
---

### Post by roemke on 2010-08-23
Hello!
I'm tried again ubuntu cause the lts version are very interesting for me.
Actual I am using 10.04 64 bit.
I try to migrate the users from a ldap-Server on opensuse to a Ldap-Server on Ubuntu. Apart from some minor problems it works fine, I followed the instructions in the official documentation. 

But, there remains one problem which leads to some "fun" for me over the last 8-10 hours:
If I try to migrate a user-password to the ldap-server which is encoded with blowfish (I think this is the default in Suse) I can't authenticate using this user and his password.
If I migrate a user with a password which is encoded with DES / crypt (the old way) I can authenticate against the user. 
If I change a userpassword with ldappasswd the password is shown as ssha (by phpldapadmin).

So I think that I need blowfish support from ldap, but I can't find a hint how to reach this. 

One more explanation: I have users with DES and Blowfish because the first users are created when the suse-System uses DES and then I upgrade the system. The next users are created using Blowfish and after that I transfer the data to the ldap system ... 
Any help would be nice
Karsten

---

