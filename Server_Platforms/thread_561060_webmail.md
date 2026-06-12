---
title: "webmail"
date: 2007-09-27
forum: Server Platforms
---

### Post by superman69 on 2007-09-27
Hi there

I have setup Virtual Users And Domains With Postfix, Courier And MySQL but I need a howtot to make a webmail serivce like squirrelmail work?

Please if some one could assit asap.

many thanks

---

### Post by superman69 on 2007-09-27
I used the following link for the setup...please could you assist me 
[http://www.howtoforge.com/virtual_users_and_domains_with_postfix_debian_etch](http://www.howtoforge.com/virtual_users_and_domains_with_postfix_debian_etch)

superman69

---

### Post by Conradle on 2007-09-27
I assume by the reference to squirrelmail, you're intending to run a php based webmail server.
Have you got Apache installed, with php support?
If not, do so.
Once that is installed, unzip the webmail server (squirrelmail, Uebimiau etc) to /etc/www. Browse to that folder via your browser at [http://localhost](http://localhost). There should be an install.php or similar file in the directory, click on that if it doesn't automatically start when you point your browser to it.
That should lead you through the setting up of the system, including creating MySQL tables etc etc.

---

### Post by ginge6000 on 2007-09-27
I used this guide - worked a treat!

[URL="https://help.ubuntu.com/community/Squirrelmail"]https://help.ubuntu.com/community/Squirrelmail
[/URL]
Ben

---

