---
title: "Enable URL Rewrite"
date: 2013-03-24
forum: Server Platforms
---

### Post by caleb12134 on 2013-03-24
I have a minecraft server that is popular. we are moving over to a new panel called spacebukkit. but upon installing it on our DellPowerEdge it says we need _URL rewrite on????_ It is run on a apache web server????

DellPower Edge with 8 gigs ram and a quad core processor.

---

### Post by LeDieu on 2013-03-24
You need to enable the rewrite module in Apache.
You can do this via the command:
```
a2enmod rewrite
```
Just make sure you restart the apache server after:
```
/etc/init.d/apache2 restart
```

---

