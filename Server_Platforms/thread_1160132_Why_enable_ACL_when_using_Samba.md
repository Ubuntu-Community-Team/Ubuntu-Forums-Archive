---
title: "Why enable ACL when using Samba?"
date: 2009-05-15
forum: Server Platforms
---

### Post by velden on 2009-05-15
Hallo!

I'm trying to setup a simple home server with Samba.

In the Ubuntu server guides v8.10 and v9.04, in the paragrapf that is called: "Securing a Samba File and Print Server", i'm "told" to enable ACL for the partition where the Samba share is on.  

See here: [https://help.ubuntu.com/9.04/serverguide/C/samba-fileprint-security.html](https://help.ubuntu.com/9.04/serverguide/C/samba-fileprint-security.html) and [https://help.ubuntu.com/8.10/serverguide/C/serverguide.pdf](https://help.ubuntu.com/8.10/serverguide/C/serverguide.pdf) (paragrapf 15.4.3.2)

The main question is: why should I enable ACL when using Samba? 

The manual tells me that linux file permissions do not map very will with the Windows ACL, but as a Linux newbe, I find this kind of vague. Any pratical examples?

Also when ACL is enabled, what is the practical importance of the chmod command as compared to setfacl?

---

### Post by koenn on 2009-05-15
with unix fylesystem permissions, you can basically assign 3 sets of access: for the owner (a user), for 1 group, and for 'all others'.
The permissions are basically read, write, execute  

With extended posix ACL, you can have, for instance, ACL's for mor than one group. You can also set more specific types of access.

It's a conceptual difference mainly ; with posix acl , you can add a practically unlimited number of user and group accounts and set ACL for them, but it quickly becomes a mess to maintain - the unix way is straightforward but may require a more complex directory tree and a different approach to accounts and their group membership to fulfill your fs security needs.

chmod and setfacl will work independently of each other but are compatible, eg getfacl will show file permissions set with chmod etc.
However, Windows file system security is not 100% posix acl compliant, so if you use posix acl to integrate into a windows environment, you'll see some unexpected behavior

[http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm)

---

### Post by velden on 2009-05-15
Thank you so much! That is a very clear and helpful reply!

---

