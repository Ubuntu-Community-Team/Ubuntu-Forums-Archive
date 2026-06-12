---
title: "php files"
date: 2010-09-10
forum: Server Platforms
---

### Post by spillage2 on 2010-09-10
ok after a few hours on this I think I'm going mad.

I have my main lucid install and and lucid install on vbox.

have installed lamp on both.

my vbox display all my php files no problem but my main set refused and just asks me if I want to donwload or open the files.

I have checked so many conf files side by side my head hurts.

Anyone have any ideas.

if I run [http://localhost](http://localhost) apache runs ok.../var/wwwis set up in my sites available file.


spill.

---

### Post by noway2 on 2010-09-10
It does not appear that Apache recognizes .php files as ones that need to go through the PHP parser.  

The most obvious questions / answer is did you restart apache after installing PHP?

Next look in your mods-enabled directory and see if php5.conf and .load are both there.  The .conf file should have something like this in it:

<FilesMatch "\.phps$">
	SetHandler application/x-httpd-php-source
</FilesMatch>

---

### Post by spillage2 on 2010-09-11
Hi,

Yes all there and correct and appache has  been restarted. 

Like I said I have 2 lucid setups so have compared so many files I feel I must just be missing something stupid

---

