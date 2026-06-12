---
title: "how to upgrade the GD library?"
date: 2009-10-06
forum: Server Platforms
---

### Post by cybershan on 2009-10-06
I just installed ubuntu server 9.04 with LAMP.   It works.

But when I install Drupal6.14,  I got below error message. Anybody knows how to fix it?  thanks in advance.



**GD Image Filtering**	Low Quality / Poor Performance
The installed version of PHP GD does not support image filtering(desaturate, blur, negate, etc). It was probably compiled using the official GD libraries from [http://www.libgd.org](http://www.libgd.org) instead of the GD library bundled with PHP. You should recompile PHP --with-gd using the bundled GD library. See [http://www.php.net/manual/en/image.setup.php](http://www.php.net/manual/en/image.setup.php). An implementation of imagefilter in PHP will be used in the interim.

**GD Image Rotation**	Low Quality / Poor Performance
The installed version of PHP GD does not support image rotations. It was probably compiled using the official GD libraries from [http://www.libgd.org](http://www.libgd.org) instead of the GD library bundled with PHP. You should recompile PHP --with-gd using the bundled GD library. See: [http://www.php.net/manual/en/image.setup.php](http://www.php.net/manual/en/image.setup.php). An implementation of imagerotate in PHP will used in the interim.

---

### Post by plutonium45 on 2009-10-06
apt-get update php-gd

---

### Post by cdenley on 2009-10-06
What's wrong with drupal from the repos?
```

sudo apt-get install drupal6

```

---

### Post by mbria on 2010-01-03
Everything explained here:
[http://groups.drupal.org/node/35764](http://groups.drupal.org/node/35764)

Until update, use imagemagick

---

