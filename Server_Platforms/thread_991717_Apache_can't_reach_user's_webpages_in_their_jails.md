---
title: "Apache can't reach user's webpages in their jails"
date: 2008-11-24
forum: Server Platforms
---

### Post by Carroarmato0 on 2008-11-24
Hi, I've set up a server where the users are isolated in their own jail.

Account **test** is situated in  /home/jails/test**/home/test/www**.

The test folder is owned by root:root

Apache needs to serve the webpages that can be found inside the www folder of the user's jailed account.

Symlinking doesn't work and I've read somewhere that entering a relative path in the Virutal Host configuration section of Apache will solve this problem.

How does a relative path look like? Or is there another way how Apache could reach does files? What should the permissions be for maintaining security high?

---

### Post by Thirtysixway on 2008-11-24
YOu should look at mod_userdir which allows users to have a public_html folder in their home directory.
You need to change the group owner of /home/test to www-user (or whichever user apache is being run as)

---

