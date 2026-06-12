---
title: "Seperated hosting"
date: 2010-07-01
forum: Server Platforms
---

### Post by nusidie on 2010-07-01
Hello everyone! (who reads this),

I've got a quistion,

I wan't to seperate my website's,

The best idea to explain this is if we look at a real hosting provider,

you have youre own folder,

you can only use youre own sessions,

so if costumer 1 /www/costumer1/

make's a session (username)

and has a page with this code: echo "".$SESSION_['username'];

and costumer 2 /www/costumer2/

make's thesame session username

and also has a page wich has this code: echo "".$_SESSION['username'];

if 1 guy goes to both website's and only at costumer 1 gets the session username created and on the page the session gets showed.

and he goes to website two (were no session is created)

the page won't show the username of website 1

so its completely seperated,

Does anyone knows how to do this?

I hope u guys understood what i was trying to say!

Thanks, Nusidie

---

### Post by upbeat.linux on 2010-07-06
What you're looking to do is supported by Apache's Virtual Host mechanism:

Apache 2 - [https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)

Virtual Hosts: [http://httpd.apache.org/docs/2.0/vhosts/](http://httpd.apache.org/docs/2.0/vhosts/)

---

