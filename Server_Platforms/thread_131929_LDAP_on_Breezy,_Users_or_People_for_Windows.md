---
title: "LDAP on Breezy, Users or People for Windows"
date: 2006-02-17
forum: Server Platforms
---

### Post by gertmul on 2006-02-17
After a fresh 5.10 Server install, and running the smbldap-scripts from [http://www.majen.net/smbldap/](http://www.majen.net/smbldap/)  the LDAP is populated with ou=Users, ou=Groups, ou=Computers, and some other...

There is however no ou=People or uid=Administrator and some more as described in the various internet sources and Samba-3 by Example book...

Do you need to run the IDEALX scripts as well? or how do you go about getting an "Administrator" in there?

---

### Post by gertmul on 2006-03-05
Found the problem!!!

During running either the nss_ldap and pam_ldap setup, it asks you to enter some information like  "dc=something,dc=com", but the textbox is already filled in with "dc=example,dc=net" AND with the cursor blinking one more to the right than it should be. So if you use the backspace key, to leave only "dc=" you actually only have "dc", and if you type now "something,dc=com" the data you entered is "dcsomething,dc=com", no "=" in there!!!

And then it does not work!

If you delete everything in the textbox (the first "d" will still show), and retype everything, it will work!!!

Thanks to Matt Oquist! ([http://www.majen.net](http://www.majen.net))

---

