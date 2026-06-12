---
title: "How do I determine what package I'm running?"
date: 2010-06-03
forum: Server Platforms
---

### Post by leesiulung on 2010-06-03
I installed Apache by using the following command:

```

sudo apt-get install apache2

```I later realized that there are two (or more versions) of Apache, MPM Worker (threadsafe) and Prefork. Since I'm trying to get both Tomcat and PHP working on the same system **I need to know what version is installed of Apache, Worker or Prefork?**

Looking in the package documentation, it said something about a virtual package... Looking inthe mods-enable directory,  I don't see anything that indicates one or the other.

**I'm also wondering if Tomcat integration can work with prefork? **

Prefork is recommended for PHP....

Please help!

---

### Post by leesiulung on 2010-06-03
Silly me, I found an article right after I posted about how to do this....

[http://articles.slicehost.com/2010/5/19/configuring-the-apache-mpm-on-ubuntu](http://articles.slicehost.com/2010/5/19/configuring-the-apache-mpm-on-ubuntu)

This is after searching for a while. Go figure!

---

