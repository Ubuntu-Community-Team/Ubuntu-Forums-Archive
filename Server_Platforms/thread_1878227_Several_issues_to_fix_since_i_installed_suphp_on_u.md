---
title: "Several issues to fix since i installed suphp on ubuntu 11.10"
date: 2011-11-09
forum: Server Platforms
---

### Post by crazycoders on 2011-11-09
I got a development machine here at work that i build using a Ubuntu 11.10 distribution. The dev environment had been built with a nice custom admin interface so that all my other collegues could add and delete sites on the machine.

The problem i hit recently was that my boss wanted me to switch from mod_php5 to mod_SuPHP. It took me several hours to understand how to make all this work and eventually i succeeded in installing it on the server, now all our sites run as the owning user and it's great. 

My Integrators are able to install WordPress and don't have issues with the user running the script, permissions are all set correctly, everyone can write everywhere they want which is critical in many CMSes.

Up to now everything seemed to be working fine until this morning, we hit several new problems since the install of SuPHP:

1) I can't use "shell" or "shell_exec" php function anymore, it seems to just blaze through and i don't get any warning or notice. This broke my webadmin to create and delete sites on the machine (I can do it manually but the integrators can't go in and create Vhosts manually)

2) When i send mail using MAIL() from php, i can send outside of my business to gmail for instance, but any SMTP server checking of email existance sudenly stopped working. I was receive a backup email everyday to my work address and my collegue just tried sending himself emails from the DEVL server and nothing comes into the workplace email. We tried changing the FROM or the SMTP server address in the php.ini nothing works.

3) Specific php.ini per site doesn't work although i've followed the instructions, so now i don't have .htaccess overrides for PHP and i don't have php.ini to override php directives...

All other problems i have seem to come from those 3 problems. Can anyone help me? I'll give you any information you need, obviously i'm not gonna copy my whole php.ini and my vhosts, it'll make a 90 page long post :) Just ask me what you need and i'll gladly print it out.

Thanks

---

