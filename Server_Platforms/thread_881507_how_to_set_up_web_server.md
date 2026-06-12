---
title: "how to set up web server??"
date: 2008-08-06
forum: Server Platforms
---

### Post by jlo-linux on 2008-08-06
i want to set up a web server in my desktop editon like what i've done in windows xp ex: inetpub/wwwroot/ then i'll just paste the web site that i made then its up..


how can i do that in my ubuntu, not using ubuntu server...

help:(

---

### Post by tinny on 2008-08-06
> **jlo-linux said:**
> i want to set up a web server in my desktop editon like what i've done in windows xp ex: inetpub/wwwroot/ then i'll just paste the web site that i made then its up..


how can i do that in my ubuntu, not using ubuntu server...

help:(

Apache is what you want. (but its very different to IIS on Windows)

The installation procedure is the same regardless of whether you use Ubuntu server or desktop.

[Apache Install]("https://help.ubuntu.com/8.04/serverguide/C/httpd.html")

---

### Post by joewilliams on 2008-08-06
look into "Xammp"

---

### Post by kennedy7 on 2008-08-06
if use use Ubuntu then type this into the terminal sudo apt-get install apache inadyn php5. Then you go to [http://dyndns.org]("http://dyndns.org") and make an acount and add host. Then you run this in the terminal inadyn -u username -p password -a yourpage.com

---

