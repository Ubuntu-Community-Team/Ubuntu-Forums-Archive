---
title: "Question about installing a lamp server"
date: 2007-01-03
forum: Server Platforms
---

### Post by fearevilleet on 2007-01-03
Hello Everyone,

I am going to be installing a lamp server by following this guide [http://www.howtoforge.com/ubuntu_debian_lamp_server](http://www.howtoforge.com/ubuntu_debian_lamp_server) that I saw on digg. I have a quick question, I already have a mysql server via a hosting company (the place I work at)  is necessary to install mysql or can I use the mysql data base which I am provided via my hosting company. I just plan I putting wordpress on it nothing big. Would everything work to have the apache setup on my local machine and the mysql server hosted remotely?

---

### Post by chrisfay on 2007-01-03
Not unless you allow remote connections to the MySQL server. It's been a long time since my servers ran on a hosting option, but it seems they may block this option. If you have shell access into your account you can try modifying the MySQL configuration manually. Again, you would probably need to contact your hosting company.

---

