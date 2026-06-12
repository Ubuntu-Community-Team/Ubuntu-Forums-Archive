---
title: "coppermine photo gallery missing GD library or ImageMagik"
date: 2007-11-28
forum: Server Platforms
---

### Post by bone2006 on 2007-11-28
I installed copermine photo gallery and it looks like it's exactly what I wanted.  The problem is that I can't upload anything.  I get an error that says:

PHP running on your server does not support the GD image library, check with your webhost if ImageMagick is installed 

During installation it asked me the path of ImageMagick and I wasn't sure what the path was, but I do have ImageMagick installed.  I'm not sure if there's a way to configure coppermine now that it's already installed or what I should do?

I have no clue how to installed GD image library for ubuntu server.  Any help is appreciated.

---

### Post by James79 on 2007-11-28
```
sudo apt-get install php5-gd
```

Make sure you restart apache for the changes to take effect.

---

### Post by bone2006 on 2007-11-29
sorry for the ignorance, but what are the commands to stop and restart apache?
Thanks in advance

---

### Post by ntom-taylor on 2007-11-29
sudo apt-get install imagemagick
sudo pecl install imagick

That should sort out imagick for you. 

restart apache 

 * Usage: /etc/init.d/apache2 {start|stop|restart|reload|force-reload}

man apache2

Hope it helps ! 

Tom

---

### Post by bone2006 on 2007-11-29
It told me that pecl wasn't installed, so I ended up doing:

sudo apt-get install php5-gd
sudo /etc/init.d/apache2 restart

everything is working now

Appreciate the help guys

---

