---
title: "looking for a admin panel like cpanel"
date: 2015-03-02
forum: Server Platforms
---

### Post by Ag_Liz on 2015-03-02
hi there
Looking for a admin panel like cpanel,  any recomendation found this page [http://www.tecmint.com/web-control-panels-to-manage-linux-servers/](http://www.tecmint.com/web-control-panels-to-manage-linux-servers/)  Not sure wichone to go with!

---

### Post by tgalati4 on 2015-03-02
If you are only managing one server, then you can set up a login script to display health status when you ssh into the machine.  Otherwise, you can set up your server to send you email or text messages when things go wrong.  If you have many servers to track, then there are several decent, open source monitor solutions to look at.

[https://www.socallinuxexpo.org/scale/13x/presentations/open-source-monitoring-landscape](https://www.socallinuxexpo.org/scale/13x/presentations/open-source-monitoring-landscape)  (you can find the video of the presentation on youtube)

Go through the list, set up each one and see which one you like.

---

### Post by gmasters on 2015-03-04
You might consider webmin. It has support for most if not all of the server administration tasks you may require. It includes support for web, email, DNS, RAID, and many others.

More info: [http://www.webmin.com/](http://www.webmin.com/)

---

### Post by volkswagner on 2015-03-04
Why do you want/need a control panel?

I'd stay away from webmin. It has a history of not playing well with ubuntu (since Ubuntu 8.04)

I have not tried any control panels, but I have been tempted to try [Ajenti]("http://ajenti.org/").

I would try to stay away from any php based controlled panels. Ask around, most pros feel
php is too vulnerable.

---

### Post by tgalati4 on 2015-03-05
Do you really need a control panel?  What you want is a decent monitor of server statistics, then login with passwordless *ssh* to fix things via the terminal.  You can play with webmin and other control panels, but they have their security issues because they are running all the time and become a vector for attack.

---

