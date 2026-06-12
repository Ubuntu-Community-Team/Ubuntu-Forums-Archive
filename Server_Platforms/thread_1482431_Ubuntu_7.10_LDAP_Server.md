---
title: "Ubuntu 7.10 LDAP Server"
date: 2010-05-13
forum: Server Platforms
---

### Post by Rokurosv on 2010-05-13
So I'm doing some tests to see if I can create a LDAP server + Domain controler with Samba on Ubuntu 7.10. It might seem weird to use such an old release but I've seen a few guides on that particular version and I thought I'd give it a tr using this guide

[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

So far I'm good until I modify the pam.d and nsswitch with auth-client, after reboot I'm unable to log in to the system and I'm forced to go into safe mode and restore the backups of those files. 

What should I be looking for to prevent this from happening? I'm assuming that it's essential to modify these files in order to enable the LDAP authentication on the server.

Thanks for your time

---

### Post by lavinog on 2010-05-16
How are you even able to install any packages with 7.10?

You might find this to be more useful:
[https://help.ubuntu.com/10.04/serverguide/C/network-authentication.html](https://help.ubuntu.com/10.04/serverguide/C/network-authentication.html)
Note: it is for 10.04.

help.ubuntu.com has some handy information.

---

