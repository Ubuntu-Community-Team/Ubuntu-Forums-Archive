---
title: "Webmin remote access"
date: 2008-07-13
forum: Server Platforms
---

### Post by hornetster on 2008-07-13
Hi, have just installed 8.04 server and trying to get Webmin (webmin_1.420_all.deb) running. Have installed it successfully and can connect remotely as the "first user" that I setup when installing, but, contrary to all the doco I have been able to find, my first user has access to only the status of Webmin.... ie Only active links are System Information and logout. Help please! :(

---

### Post by Thirtysixway on 2008-07-13
Can you login as your system username, the one you use to login to Ubuntu?

---

### Post by hornetster on 2008-07-13
Yep, "and can connect remotely as the "first user" that I setup when installing" so everything is working in Webmin, it's just the permissions (sudo) thing for some reason doesn't appear to be working.... Have tried reinstalling.
John.

---

### Post by sil3nt on 2008-07-14
You should have access to all the functions of webmin by using your Ubuntu UN and PW.

Login into Webmin click on Webmin in the left hand column and choose "Webmin Users" click on your username and you can change what thinsg you have access too. 

Failing that login as root you should then have access to all the functions of webmin and be able to elevate the privileges of your standard users.

---

### Post by hornetster on 2008-07-14
Ok, the gremlins have been in the system... Have done a full uninstall and reinstall, and, surprise, surprise, it is now working.... 
Well, I'll take the blame, although I don't know why.. May not have been a permission thing, as the Webmin screen only had System info and logout icons, no other modules etc....
Dunno!!
Thanks for the help!:lolflag:

---

