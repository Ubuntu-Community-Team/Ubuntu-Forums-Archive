---
title: "run a web server"
date: 2015-11-25
forum: Server Platforms
---

### Post by debjyoti2 on 2015-11-25
hi, im running a 15.4 ubuntu [vivid vervet] desktop edition and i installed apache 2 on it....
can any one tell me how to copy my website files to www folder that every body inthe internet can access..?

---

### Post by QIII on 2015-11-25
Before going any further, a few questions:

Did you know that support for Vivid runs out in January?

Is this in your home and, if so, does you ISP allow this?

Are you prepared to deal with security?

Do you realize that you should run a web server with the very least number of services and that a desktop environment exposes more attack surface to those with ill intent?  Do you realize that this is why Ubuntu offers a server version?

---

### Post by Lars Noodén on 2015-11-25
> **debjyoti2 said:**
> hi, im running a 15.4 ubuntu [vivid vervet] desktop edition and i installed apache 2 on it....
can any one tell me how to copy my website files to www folder that every body in the internet can access..?

As long as you stay with static XHTML + CSS then security is more or less built in.  The same cannot be said of ventures involving [PHP](http://eev.ee/blog/2012/04/09/php-a-fractal-of-bad-design/) or other languages.  

If you are sticking with static XHTML + CSS, then just move your files to /var/www/html and you are set.  Everything you put there will be visible to the net.  So only put things there that you intend to stay public.  If you are the only user logging in to that machine then you can get write permission by taking ownership of the directory:

```

sudo chown debjoyti2 /var/www/html/

```

If you want to share write access to the web files with other users, then you'll have to use groups.  

As far as the version goes, 14.04 is supported through 2019 and is thus a better choice than 15.04.

---

### Post by kolumcaj-silvi on 2015-12-09
you can copy your files via terminal using this command: sudo mv (to move) or cp (to copy) /path/to/dir/ /var/www/html/ and you can chown them to apache user with this command: sudo cd /var/www/html/ and than chown -R www-data:www-data * it will chown everything in that folder to apache user and group

---

