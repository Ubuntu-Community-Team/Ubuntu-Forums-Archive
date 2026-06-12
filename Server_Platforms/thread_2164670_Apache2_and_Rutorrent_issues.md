---
title: "Apache2 and Rutorrent issues"
date: 2013-08-01
forum: Server Platforms
---

### Post by albert_wesker2 on 2013-08-01
I am running Ubuntu Server 10.04 and Have Rutorrent installed via an easy to use installation script.

I want to be able to run rutorrent and my own website off of the same server at the same time. but when ever i try to access [www.blah.com](www.blah.com) it automatically takes me to the rutorrent log in page. How can I make it so I type in [www.blah.com](www.blah.com) it takes me to my web site and typing in rutorrent.blah.com takes me to the rutorrent sign in page

---

### Post by Hexxus on 2013-08-01
I assume you're running apache2 on your server. 

Check out the sites-enabled in /etc/apache2/sites-enabled and your default.

You'll probably have a bit of learning like I did in regards how to use apache vs iis to host multiple sites on 1 ip address.

Heres this information that I used to accomplish that, which is what I think you're trying to do.

[https://library.linode.com/web-servers/apache/installation/ubuntu-12.04-precise-pangolin](https://library.linode.com/web-servers/apache/installation/ubuntu-12.04-precise-pangolin)

---

### Post by albert_wesker2 on 2013-08-01
Well I got things to work and got my website up and running with out rutorrent complaining. I did this with the help of this [https://help.ubuntu.com/10.04/serverguide/httpd.html](https://help.ubuntu.com/10.04/serverguide/httpd.html)

anyways my website [https://globalprivacysolutions.pw/](https://globalprivacysolutions.pw/) is now up

I will probally hang around here for a while as I may need help in the future.

---

### Post by albert_wesker2 on 2013-08-01
ok I have issues now since i created the ssl cert for globalprivacysolutions when ever i try to access rutorrent via https it automatically takes me to my website instead of rutorrent


...Fixed...

Had to add another line for NameVirtualHost *80  in port.conf

---

### Post by Hexxus on 2013-08-02
> **albert_wesker2 said:**
> ok I have issues now since i created the ssl cert for globalprivacysolutions when ever i try to access rutorrent via https it automatically takes me to my website instead of rutorrent


...Fixed...

Had to add another line for NameVirtualHost *80  in port.conf

Yeah, that'll happen. I had a few times where I thought things we're good to go then I stumbled upon problems. 

Glad to hear its up and running!

---

### Post by albert_wesker2 on 2013-08-07
edit

---

