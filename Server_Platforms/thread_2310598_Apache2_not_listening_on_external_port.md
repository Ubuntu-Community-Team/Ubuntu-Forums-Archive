---
title: "Apache2 not listening on external port"
date: 2016-01-20
forum: Server Platforms
---

### Post by Triffgits on 2016-01-20
I just need a little help troubleshooting this, I'm not well-versed in apache.

I haven't done much, so I'll walk you through the couple changes I've made to the config files and you can tell me where I made a wrong turn.

First I installed the apache2 package, and navigated to my /etc/apache2 directory. Next, in the file ports.conf, I edited the line that read **Listen 80** and changed it to **Listen 3000**. I switched to the directory /etc/apache2/sites-available and edited 000-default.conf, the line that read **<VirtualHost *:80>** was changed to **<VirtualHost *:3000>**. I then forwarded the port for the server on my router and tested my external ip with the port 3000. It returns a connection-refused error.

Thoughts?

---

### Post by darkod on 2016-01-20
And does it work from inside your home network?

Also, did you confirm apache is listening on 3000? You can check running services with:
```
sudo netstat -plunt
```

Also, is there a firewall active on the server? I assume not, otherwise you will have to open port tcp/3000 for incoming traffic of course.

---

### Post by Habitual on 2016-01-20
Did the OP restart apache after editing?

---

### Post by Triffgits on 2016-01-20
I restarted the whole machine after editing (because it's actually a raspberry pi, very quick to reboot), it does work on my local network just fine, I get the default apache test page from my desktop computer and my smart phone when I connect via the local ip. I confirmed that apache was listening on port 3000 using [COLOR=#222426][FONT=Consolas]sudo netstat -napW | grep apache. [/FONT][/COLOR]And no, there is no firewall running on the server.

---

### Post by Triffgits on 2016-01-20
So guys, this is embarrassing, but I just assumed my router defaulted to TCP and didn't check. My forward was UDP and upon switching to TCP it works fine. Consider this solved.](*,)

---

### Post by Habitual on 2016-01-20
Good job and well done!

---

