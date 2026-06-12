---
title: "configuring Apache 2/Ubuntu 7.04 problem"
date: 2007-09-03
forum: Server Platforms
---

### Post by Priswell on 2007-09-03
I am using Ubuntu 7.04, and I am fairly new to linux. 

I am trying to set up Apache Server 2 and am having a problem with that. I installed Apache by using Synaptic and got the "It Works!" page. then I thought to edit the page. The page would not save. So I edited it as root, and it did save, but now Apache will not read it. Permissions are set for 644, but even when they are set at 777, it still will not read it. Instead of getting my edited "It works" page, if I go to [http://localhost/](http://localhost/), I get "Index of /". If I try to go to [http://localhost/index.html](http://localhost/index.html), I get Page Not Found.

I have read many, many help files here, on the apache site and through google and have not found any leads as to what the problem might be.

The error log is empty. I tried to attach a copy of my configuration file, but that didn't seem to work, so I uploaded it to my domain

[http://priswell.com/apacheconfigfile.txt](http://priswell.com/apacheconfigfile.txt)

---

### Post by lightstream on 2007-09-03
you can go to the /var directoy in a console, and type **sudo chmod 666 www** 

Then you can create directories and files in www as a normal user, so they are accessible to apache.

---

### Post by Priswell on 2007-09-03
Thank you for responding. 

However, now I'm getting 403 "Forbidden"

---

### Post by inphektion on 2007-09-03
I'd chown it to www-data to be sure.

---

### Post by Priswell on 2007-09-04
*I'd chown it to www-data *

I don't know how to do that.

---

### Post by breakaway on 2007-09-09
chown -R -v www-data /path/to/config/file

---

### Post by southernman on 2007-09-09
FYI - the default apache install, acutally severs it's "It works" page from the /var/www/apache2 directory... not the standard /var/www

If you setup and enable a new site, then it will look in /var/www for an index.extension(html, php, cgi, shtml...) page. If you do "ls /var/www you won't find a index page there... you have to create one. ;)

The reason you got the "403 Forbidden" error is you most likely have indexes turned off (-Indexes) in either apache2.conf or the newly enabled site conf file. Which you should do unless you want to server a directory listing to the world that people can browse. If you'll create a simple text file in /var/www called index.html, when you surf to localhost or whatever you' should see it working now.

AFAIK, telling you to chmod /var/www to 666 is simply not correct. From my readings, the /www directory (and all directories within (for your website) should be chmod 755. Individual files within those directories should be chmod to 644 at the very most.

Perhaps bohdi.zazzen, Mr.C, koenn, Herman AB or some of the others more expeienced can correct me if I am wrong. The only thing I dislike worse than seeing improper info being strewn about, is doing so myself! ;) However, I am pretty confident on the info I've shared above.

Hope that helps you

PS. I don't have my server on atm so above where I mention /var/www/apache2 may actually be /var/www/apache2-default

---

