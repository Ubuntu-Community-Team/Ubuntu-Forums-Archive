---
title: "Package php5-imagick is not available"
date: 2008-09-18
forum: Server Platforms
---

### Post by angstsix on 2008-09-18
Hello!

I'm a bit of a n00b:confused: whenit comes to Ubuntu. ( just so u know ).

I'm running Apache 2.0 w/PHP 5.1.2 and i'm trying to install ImageMagick using this command:

apt-get install php5-imagick

but I get this error:

root@harp:/home/kscott# apt-get install php5-imagick
Reading package lists... Done
Building dependency tree... Done
Package php5-imagick is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package php5-imagick has no installation candidate


I've never seen this error before, does anyone know how I can correct this?

thanks in advance for your time!
cheers,
-Ken

---

### Post by condonm on 2008-10-03
Try running this first:
```
$ apt-get install imagemagick
``` 
Then Run
```
$ apt-get install php5-imagick 
```
And then restart Apache
```
$ /etc/init.d/apache2 restart
```

Hope this helps, if you haven't already figured it out!

---

### Post by windependence on 2008-10-04
You should probably run:

```
sudo apt-get update
```

First before you install your ImageMagic packages.

-Tim

---

### Post by volkswagner on 2008-11-10
I would like to get this for 6.06.  It is not available.  I see it is in later repositories.

What can I do.

I ran update, still no go.

Odd that the imagemagick package is in 6.06 but not th php5 module.  I see the php4 version is available.  Not sure if I should install that.

What do you all think?

Can I add a newer repository temporarily for this?


```

sudo apt-get install php5-imagick
Reading package lists... Done
Building dependency tree... Done
Package php5-imagick is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package php5-imagick has no installation candidate
```



```
 sudo apt-get install php4-imagick
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  apache-common libapache-mod-php4 libzzip-0-12 php4-common
Suggested packages:
  apache apache-ssl apache-perl
The following NEW packages will be installed:
  apache-common libapache-mod-php4 libzzip-0-12 php4-common php4-imagick
```

---

### Post by windependence on 2008-11-10
PHP 5 wasn't out yet when 6.06 was released. There are ways you could do this but none of them are pretty. If it was me, I would downgrade to PHP 4 and use the old packages but I am sure there will be some people here who won't agree. Anything over version 4 is usually OK.

-Tim

---

### Post by volkswagner on 2008-11-11
Well I needed the package for linPHA.  linPHA recognized the imagemagick as installed.  I have uploaded some photos.  I have yet to see anything not functioning.  

Time will tell.

---

