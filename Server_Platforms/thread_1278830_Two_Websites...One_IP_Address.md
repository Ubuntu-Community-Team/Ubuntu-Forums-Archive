---
title: "Two Websites...One IP Address"
date: 2009-09-30
forum: Server Platforms
---

### Post by jquintana on 2009-09-30
Hello, all.

I found your forum via a google search for running multiple website on one apache server. The link I dug up was this one: [http://ubuntuforums.org/showthread.php?t=754001](http://ubuntuforums.org/showthread.php?t=754001)

The problem I am having is that when I create my two virtual hosts in webmin I am only able to access one of the sites.

I have deleted the two virtual hosts, for now, so that I can access both of my sites.

Any help is greatly appreciated.

I can do this on IIS all day long, but am new to Linux/Apache.

Thanks!

---

### Post by hessiess on 2009-09-30
Apache is configured with text files and its best to do it that way, not using a GUI wrapper. This sounds like a problem I was having, and in my case it was the lack of the line ```
NameVirtualHost *
``` before the vhost definitions.

[http://httpd.apache.org/docs/1.3/vhosts/name-based.html](http://httpd.apache.org/docs/1.3/vhosts/name-based.html).

---

### Post by Littleweseth on 2009-09-30
Have you tried configuring vhosts manually (without using webmin?) As compared to mucking around with a GUI interface, it can actually be *much* easier to just wade in and edit the config files manually.

Here's some pointers :

1) Apache2 vhost documentation :
[http://httpd.apache.org/docs/2.0/vhosts/](http://httpd.apache.org/docs/2.0/vhosts/)

2) Apache2 'VirtualHost Examples'(examples of configurations for common setups) :
[http://httpd.apache.org/docs/2.0/vhosts/examples.html](http://httpd.apache.org/docs/2.0/vhosts/examples.html)

3) [http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412) <- a HOWTO for exactly what you want to do, with some fairly good explanations of what's actually going on. (Read this one!)

Post back with any more questions.

- L.

---

### Post by i.r.id10t on 2009-09-30
If you will be running more than a couple of websites you may want to look at using ISPConfig - very easy to use, lets you set up mail, dns, web, ftp/ssh/cron etc.

---

### Post by jquintana on 2009-10-01
> **hessiess said:**
> Apache is configured with text files and its best to do it that way, not using a GUI wrapper. This sounds like a problem I was having, and in my case it was the lack of the line ```
NameVirtualHost *
``` before the vhost definitions.

[http://httpd.apache.org/docs/1.3/vhosts/name-based.html](http://httpd.apache.org/docs/1.3/vhosts/name-based.html).I have tried configuring the httpd.conf file but it didnt work, so I tried webmin.

I believe I tried NameVirtualHost * already, but will try again.

Thanks!

---

### Post by stlsaint on 2009-10-01
i hope i understand what you are asking so i will answer as i see it...if you have server with vps in it you need to setup port forward on port 80 to two seperate IP's than you are looking for a reverse proxy...
most use many other options like load balance, reverse proxy etc etc...
you can look into pound, squid, nginx just for starters...i use pound for now...all work well with Linux.

---

### Post by jquintana on 2009-10-01
I got it working. In case someone else stumbles upon this, make sure if you add NameVirtualHost *:80 that you also specify <VirtualHost *:80>. I was just doing <VirtualHost *>.

Thanks!

---

