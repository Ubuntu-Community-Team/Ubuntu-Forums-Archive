---
title: "Installing LAMP"
date: 2012-04-02
forum: Server Platforms
---

### Post by roffisserver on 2012-04-02
I am setting up a new server and am going to put Lamp on it. Does anyone have any tips on installing it and setting it up?:popcorn:

---

### Post by bubylou on 2012-04-02
You can install it on first install or just use the tasksel command if you have already installed Ubuntu. What will you be using the LAMP for. There are plenty of guides and resources available for using a LAMP server. Just use Google and when Google cant help there's always the helpful community here.

---

### Post by Volens on 2012-04-03
The server edition makes getting the base setup pretty easy. You simply select LAMP server when it displays the package menu. Look around for some apache tutorials. Depending on what you are looking to do, you may want to change Apache so that each user has a public folder rather than having the central /var/www directory. I haven't done it, but it makes it easy if you're just looking to mess around with HTML.


Check out the apache docs as well:
[http://httpd.apache.org/docs/2.4/](http://httpd.apache.org/docs/2.4/)

---

### Post by Cheesemill on 2012-04-03
[http://library.linode.com/lamp-guides/ubuntu-11.10-oneiric](http://library.linode.com/lamp-guides/ubuntu-11.10-oneiric)

---

### Post by mörgæs on 2012-04-03
If you are new in this and want a system for getting experienced, you just need the commands

```
sudo apt-get install tasksel
sudo tasksel install lamp-server
```

After that you have a server where localhost points to /var/www.

---

### Post by zeljkojagust on 2012-04-03
I would go with Cheesemill's link. Linode has excelent guide library.

---

### Post by roffisserver on 2012-04-03
Thanks for all of the tips! I think I will install LAMP manually.

---

