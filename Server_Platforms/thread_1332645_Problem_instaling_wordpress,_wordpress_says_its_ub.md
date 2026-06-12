---
title: "Problem instaling wordpress, wordpress says its ubuntu security"
date: 2009-11-20
forum: Server Platforms
---

### Post by mleger on 2009-11-20
my [http://localhost/wordpress](http://localhost/wordpress) brings up the following page
The config file for the specified host is not under an allowed path

the guys over at word press are saying this is a ubuntu file permissions issue, but thats where the help ends.

url: [http://wordpress.org/support/topic/333894?replies=2](http://wordpress.org/support/topic/333894?replies=2)

any help would be greatly appreciated.

---

### Post by cariboo on 2009-11-21
For now I would set all the permissions to 777:

```
sudo chmod -R 777 /usr/share/wordpress
```

If I remember correctly Wordpress will tell you what permissions are needed before going live

---

### Post by mleger on 2009-11-21
yup, did that still no change.

---

### Post by Queue29 on 2009-11-22
If you don't mind starting from scratch again, I highly recommend [http://www.turnkeylinux.org/wordpress](http://www.turnkeylinux.org/wordpress) . It works fantastically for me, has webmin, SSL, wordpress, and postfix all pre-configured.

---

### Post by mleger on 2009-11-23
can't

im using rack space and can't control the os like that. i can rebuild but id need to install packages only.

---

### Post by agger on 2009-11-24
> **mleger said:**
> can't

im using rack space and can't control the os like that. i can rebuild but id need to install packages only.

I'm having the same problem with Ubuntu server and I still can't figure out a solution. I've chmod'ed everything in /usr/share/wordpress and /etc/wordpress.

---

### Post by agger on 2009-11-24
> **agger said:**
> I'm having the same problem with Ubuntu server and I still can't figure out a solution. I've chmod'ed everything in /usr/share/wordpress and /etc/wordpress.

I found out the solution: I had config'ed mysql with "localhost" as my hostname, so I ran this command:

```
sudo bash /usr/share/doc/wordpress/examples/setup-mysql -n wordpress localhost
```

However, I was working on my test server and thus accessing the config page through an URL which was not "localhost" (specifically, it was "draupadi.modspil.dk", but that is hardly important).

So the solution was to do:

```

cd /etc/wordpress/

sudo cp config-localhost.php config-draupadi.modspil.dk.php

sudo chown www-data config-draupadi.modspil.dk.php 


```

Et voila! I suppose if you substitute your own parameters it'll work for you too.

---

### Post by Thirtysixway on 2009-11-24
Is there a benefit to using a wordpress package instead of downloading wordpress and installing yourself?  Seems to me that if you're paying for hosting from rackspace, you know what you're doing... :)

---

### Post by agger on 2009-11-25
> **Thirtysixway said:**
> Is there a benefit to using a wordpress package instead of downloading wordpress and installing yourself?  Seems to me that if you're paying for hosting from rackspace, you know what you're doing... :)

If you use the Wordpress package you can get updates through apt-get. However, you can't set up per-user blogs, so you can only use the Wordpress package for ONE blog. This is illogical in a multi-user environment like a Web server, I think, but then I should probably say that to the Wordpress developers, or do the coding myself :-)

---

### Post by mleger on 2009-11-25
Thanks, i managed to solve my problem by following a full guide as opposed [https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

---

### Post by Thirtysixway on 2009-11-25
> **agger said:**
> If you use the Wordpress package you can get updates through apt-get. However, you can't set up per-user blogs, so you can only use the Wordpress package for ONE blog. This is illogical in a multi-user environment like a Web server, I think, but then I should probably say that to the Wordpress developers, or do the coding myself :-)

Ah okay. the updates via apt-get would be a big plus in that situation. :popcorn:

---

### Post by spikyjt on 2009-11-25
I've always found installing WP "manually" - ie straight from the download from wordpress.org. It's so easy to install anyway and handles its own updates. This gives you much greater flexibility and you can ensure you always have it updated straight away, without waiting for someone to build a Debian package for it. In fact the only web app I've found to work well from the OS package is phpmyadmin.

---

