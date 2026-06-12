---
title: "[SOLVED] [apache2] virtual name-based hosting - defaults to wrong directory"
date: 2008-09-10
forum: Server Platforms
---

### Post by yong_sa on 2008-09-10
Hello:

I've been trying to set up my apache2 virtual name-based host.

I have two domains: 
foo.com 
sub1.foo.com

on different directories.

Works great. But when I add a third one (sub2.foo.com) and enable it,

sub2.foo.com works.

but

[www.foo.com](www.foo.com) loads the home page for sub2.foo.com 

sub1.foo.com and foo.com load up properly.

What I would like is to have [www.foo.com](www.foo.com) load up the home page for foo.com, just like any regular website.

Any ideas on how to fix this? Please tell me what config files you would like me to post and I'll put it up.

Thanks very much for your help.


Sincerely,

yong_sa

---

### Post by mbeach on 2008-09-10
You may want to look up the Serveralias directive and have something like:
ServerName [www.foo.com](www.foo.com)
ServerAlias foo.com

Perhaps you have serveralias of *.foo.com somewhere?

post the output of:
```

grep -i documentroot /etc/apache2/sites-available/*
```
and
```

grep -i servername /etc/apache2/sites-available/*
```
and
```

grep -i serveralias /etc/apache2/sites-available/*
```

---

### Post by yong_sa on 2008-09-11
Thanks! Here's what I have.

```

blah@mycomputer:~$ grep -i documentroot /etc/apache2/sites-available/*
/etc/apache2/sites-available/default_old:       DocumentRoot /var/www/
/etc/apache2/sites-available/sub2.foo.com:DocumentRoot /var/sub2.foo.com
/etc/apache2/sites-available/foo.com:DocumentRoot /var/www
/etc/apache2/sites-available/sub1.foo.com:DocumentRoot /var/sub1.foo.com


blah@mycomputer:~$ grep -i servername /etc/apache2/sites-available/*
/etc/apache2/sites-available/sub2.foo.com:ServerName sub2.foo.com
/etc/apache2/sites-available/foo.com:ServerName foo.com
/etc/apache2/sites-available/sub1.foo.com:ServerName sub1.foo.com

blah@mycomputer:~$ grep -i serveralias /etc/apache2/sites-available/*
/etc/apache2/sites-available/sub2.foo.com:ServerAlias http://sub2.foo.com
/etc/apache2/sites-available/foo.com:ServerAlias www.foo.com
/etc/apache2/sites-available/sub1.foo.com:ServerAlias http://sub1.foo.com

```

---

### Post by windependence on 2008-09-11
You need to disable the default site :

```
sudo a2dissite default
```

Don't forget to enable each of your vhosts and then restart Apache:

```
sudo /etc/init.d/apache2 reload
```

-Tim

---

### Post by yong_sa on 2008-09-11
The default site is disabled (ie. no links in the sites-enabled directory). Do I need to delete the default_old file in the sites-available directory?

---

### Post by windependence on 2008-09-11
Well I don't think that's the problem but it certainly couldnt hurt.

Can you post your apache2.conf and your sites-available file(s)?

-Tim

---

### Post by mbeach on 2008-09-11
i'd probably try dropping the http:// in the serveralias directive.

---

### Post by volkswagner on 2008-09-11
I believe it is related to the "on address" directive.  I did not know what the syntax meant in the default config file.

I found it easier to use webmin and select 'default', or 'any' for the "on address directive".  

If I specified an ip or tried the <ServerName *> directive in the config file I would get overlap errors on apache restart.  I would also have the wrong site load.

---

### Post by inphektion on 2008-09-11
> **mbeach said:**
> i'd probably try dropping the http:// in the serveralias directive.

yes get rid of the http:// in the serveralias.

---

### Post by yong_sa on 2008-09-11
Dropping the http:// in the server alias worked! Thanks so much for your help! Now the web server passes the wife test! woohoo! Now she can get into the world of blogging.

---

### Post by mbeach on 2008-09-12
laughed at that - read it as 'wifi test' and wondered if I completely misunderstood something.  Got it know - 'wife test'.  Understand fully.

if you get a chance mark the post as solved using the thread tools.

---

