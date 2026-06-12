---
title: "PHP pages not running - triggering download box instead"
date: 2005-11-06
forum: Server Platforms
---

### Post by Sleeper Service on 2005-11-06
I've had this problem before and fixed it, but I really can't see what I've done wrong this time.

Apache is running fine, and will display normal webpages using http://localhost/etc...

But if I open a PHP page, I'm prompted to download an application/php file.

I've done a fresh install of the following, using synaptic:

apache 1.3.33-8
apache-common 1.3.33-8
apache2-utils 2.0.54-5ubuntu2
libapache-mod-php4 4.4.0-3
php4 4.4.0-3
php4-common 4.4.0-3
php4-gd 4.4.0-3
php4-mysql 4.4.0-3
php4-ps 1.3.1-5.1ubuntu1

I'm not sure what I've missed - all the files I'm attempting to open are readable and executable...

Any clues?

---

### Post by paddyg on 2005-11-06
why didn't you just use apt-get?
```
sudo apt-get install apache2
sudo apt-get install php4
```

---

### Post by JogerNaut on 2005-11-06
Edit your httpd.conf file.
Find and uncomment/add these lines ```
LoadModule php4_module libexec/libphp4.so
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps
```

---

### Post by Sleeper Service on 2005-11-06
@ paddyg:  Thanks for the advice.  I use synaptic because I need Apache 1.3 rather than 2, and I also need a few other things; gdlib for one. I just find synaptic a bit easier for this because I can browse the various packages available.

Also, I think you'll find that Synaptic is simply a front-end for apt-get, so there shouldn't be any difference in the results.

---

### Post by Sleeper Service on 2005-11-06
@ Jogernaut:

Thanks for that - seems we might be near the heart of the problem.  I edited /etc/apache/httpd.conf as advised, then stopped apache.

Now, when I try to restart apache, I get the following:

```
$ sudo /etc/init.d/apache start
Configuration syntax error detected. Not reloading.

Syntax error on line 205 of /etc/apache/httpd.conf:
Cannot load /etc/apache/libexec/libphp4.so into server: /etc/apache/libexec/libphp4.so: cannot open shared object file: No such file or directory
```

So still no cigar...

---

### Post by Sleeper Service on 2005-11-06
And further oddness:

To try and get around the above problem, I created a symlink called libexec in /etc/apache/ which pointed to /usr/lib/apache/1.3 - where libphp4.so exists.

This allows me to start Apache again - so I'm assuming the PHP4 module is being loaded - but I'm still being asked to download PHP files by my browser...

](*,)

---

### Post by Sleeper Service on 2005-11-06
OK - a bit more expermentation shows that PHP IS basically working - the problem is with me using "localhost".

If I use http://localhost/etc...  PHP pages don't seem to work.

If I use http://192.168.0.2/etc...  (that's the IP of this machine on my LAN) PHP works just fine.

If I use http://chihiro/etc...  (that's the hostname of this machine) PHP also works fine.

So can anybody suggest why "localhost" seems not to work?  I've had a look at my network settings, and everything seems in order...

---

### Post by LordHunter317 on 2005-11-06
[QUOTE=Sleeper Service]To try and get around the above problem, I created a symlink called libexec in /etc/apache/ which pointed to /usr/lib/apache/1.3 - where libphp4.so exists.[/quote]What he told you was a RedHat-ism.  You should use the full path in Debian.

As for your localhost issues, post your httpd.conf.

---

### Post by dbee on 2005-11-07
> 
Edit your httpd.conf file.
Find and uncomment/add these lines
```

LoadModule php4_module libexec/libphp4.so 
AddType application/x-httpd-php .php 
AddType application/x-httpd-php-source .phps

```


... aren't those lines in apache.conf ??  ... should be the same difference as long as they are in their somewhere (... and only there once).

... is it possible that you have php compiled in statically and that you're trying to link it in dynamically at the same time ?? Find your apache binary - I think it's labelled httpd for apache1.3. Then run it with the -l switch like I do below with the apache2 binary...
```

/usr/sbin/apache2ctl -l

```
then try your version of using the -t switch
```

/usr/sbin/apache2ctl -t

```
to run a synatx check on your config. You may think about editing out the LoadModule php4_module libexec/libphp4.so bit, depending on your above results.

Hope this helps

---

### Post by slipjig on 2005-11-07
[QUOTE=LordHunter317]As for your localhost issues, post your httpd.conf.[/QUOTE]
Didn't want to flood by including it in a post, and was too big to be included as attachment.  So I've posted it here: [http://flet.org/httpd.conf.txt](http://flet.org/httpd.conf.txt)

---

### Post by Sleeper Service on 2005-11-07
Ooops - I posted that as the missus :oops:  (blasted Opera magic wand!)

[http://flet.org/httpd.conf.txt](http://flet.org/httpd.conf.txt) is, in fact, *my* httpd.conf file!

---

### Post by LordHunter317 on 2005-11-07
[QUOTE=dbee]Find your apache binary - I think it's labelled httpd for apache1.3.[/quote]Nope.

> to run a synatx check on your config.Won't help.

OP:
Post your modules.conf as well, something is amiss here.  And any relevant files in conf.d/, please.

---

### Post by andlinux21 on 2005-12-14
I have been searching the forums too for an answer i cant get my mambo site to load the index.php file so I can set it up I hope they find a solution. I don't want to go back to SuSE unless i just have too....

---

