---
title: "really simple problem from Apache newbie"
date: 2010-04-30
forum: Server Platforms
---

### Post by jcorden on 2010-04-30
Hi
I have just completed a LAMP installation on my Ubuntu (9.10) pc. Everything seems to be working fine and I can open test pages and interact with mySQL using phpmyadmin.

Currently I can only view html files (using Firefox) that are saved in the following directory on my pc.

/var/www 

using the following url

[http://localhost/](http://localhost/)

the html files that I would like to view are in this directory on my pc

home/james/webdevel

How do I redirect Apache (or what url do I use) so that I can view and process html and php files that reside in the webdevel directory? Am I correct in thinking I need to edit my httpd.conf file and where does this live?

Thanks

---

### Post by Bachstelze on 2010-04-30
> **jcorden said:**
> 
Am I correct in thinking I need to edit my httpd.conf file and where does this live?

Not necessarily. Apache cannot normally access files that are outside its [font=monospace]DocumentRoot[/font]. There are several ways to achieve what you want, some of which don't require editing the Apache config file

-> If you don't use [font=monospace]/var/www[/font], you can just change your [font=monospace]DocumentRoot[/font] to the directory your files are in. Of course make sure you give Apache permission to access it.

-> You can also create a subdirectory of [font=monospace]/var/www[/font] (e.g. [font=monospace]/var/www/webdevel[/font]) and do a [font=monospace]mount -o bind /home/james/webdevel /var/www/webdevel[/font]. This will make the directory accessible by both names, and you should be able to access it at [http://localhost/webdevel](http://localhost/webdevel). Obviously, you can also do [font=monospace]mount -o bind /home/james/webdevel /var/www[/font].

-> Creating an alias in your Apache config file, like:

```
Alias /webdevel /home/james/webdevel
```

This will also make your files accessible at [http://localhost/webdevel](http://localhost/webdevel).

And a lot of others, but you probably want to look at one of those three.

---

### Post by jcorden on 2010-04-30
Thanks for your help. I will try these.

Will there also be problems accessing mySQL from the webdevel directory?

Basically I want my webdevel directory to replicate the home directory on the webserver that I eventually use to host the site, so that when I copy the files to the webserver I can just upload the entire contents of the webdevel directory. Will this influence the best approach?

---

### Post by Bachstelze on 2010-04-30
> **jcorden said:**
> 
Will there also be problems accessing mySQL from the webdevel directory?

No, MySQL is totally independent of your Web server structure, and it not affected in any way by the location of the PHP file that accesses it.

---

### Post by krodrigue on 2010-05-01
Why not just copy the files to /var/www

cp -r /home/james/webdevel /var/www

---

### Post by Kellemora on 2010-05-01
Hi JC

Here is what I was instructed to do as being the safest method.

Open gedit and navigate your way to /var/www
then simply type sudo ln -s /home/me/webfiles/nameofyourfile.......
This will link the folder in your /home/me/webfiles directory to /var/www...
Works GREAT and keeps the BLOAT out of your system file area too!
And if you back up your /home directory, you've also saved all your web page work at the same time!

TTUL
Gary

---

