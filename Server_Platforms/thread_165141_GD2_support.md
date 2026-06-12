---
title: "GD2 support"
date: 2006-04-24
forum: Server Platforms
---

### Post by Coruba67 on 2006-04-24
Hi guys,

Have setup a little web server for a lan that a few mates and I run however was really needing GD2 support for apache on there...  Was wondering what I need to do to get this happening..

thanks in advance.

---

### Post by fdoving on 2006-04-24
I assume you mean PHP with gd support? 

If you use php5:
```

apt-get install php5-gd

```

PHP4:
```

apt-get install php4-gd

```


- Frode

---

### Post by TooRight on 2007-08-18
I'm having problems with this myself.

When I type that into konsole I get:

```
php5-gd is already the newest version.
```

Is there some configuring i should be doing?

---

### Post by Sir P on 2007-12-06
You have php-gd installed, you need php-gd2

apt-get remove php-gd
apt-get install php-gd2

---

