---
title: "ServerName being ignored in http-vhosts.conf"
date: 2007-12-07
forum: Server Platforms
---

### Post by dshuck on 2007-12-07
For a little background, I have had this development system running for some time under 7.04 using a hand-compiled httpd 2.2.6.   I am also using jk_mod and passing some of the requests off to a tomcat application.  I had no problems whatsoever with a vhosts file with probably about 10 different sites in it.  Each site was added to my 127.0.0.1 in my hosts file, with a matching entry in the vhosts.  Subsequently, [http://devsite1](http://devsite1) would go to /.../htdocs/devsite1/www and [http://devsite2](http://devsite2) would go to /.../htdocs/devsite2/www and life was good.

Recently I was trying to set up a network install for Gutsy by putting the CD in this machine and letting another machine access it using a "boot from network" option.  Unfortunately I got in too much of a hurry (usually where problems arise) and in a long string of >sudo apt-get install [bunch of apps] I missed a sneaky little "apache2".  So in addition to my compiled version I accidentally installed apache2 from a repo.  I immediately realized my mistake and did an apt-get autoremove, then went through the system making sure to the best of my ability that there were no remnants.  

However, since that day, my vhost ability is hosed.   The evidence is that no matter what servername is in the url, any request automatically goes to the first website in my http-vhosts.conf file.  Additionally,  when I start up apache, I receive the following error(s):
```

dshuck@dshuck-laptop:/$ sudo /etc/init.d/httpd restart
[Fri Dec 07 11:36:58 2007] [warn] _default_ VirtualHost overlap on port 80, the first has precedence

```

I receive one warning for the overlap for each additional site in my http-vhosts.conf file beyond the first entry.

Today I finally ripped the guts out, removing apache, recompiling apache, recompiling tomcat-connectors, re-setting up jk_mod, etc.  After all of that, I ended up in the same boat.

For a further and completely simple example of the failure, in this scenario, any request goes to /usr/local/apache2/htdocs/illudium
```

<VirtualHost *:80>
    	ServerName illudium
	DocumentRoot /usr/local/apache2/htdocs/illudium
</VirtualHost>

<VirtualHost *:80>
    	ServerName cd1
	DocumentRoot /usr/local/apache2/htdocs/cd1
</VirtualHost>

```

If I swap the order, all requests go to cd1.  The bottom line is that it appears that apache is ignoring my ServerName attribute all together.  Does anyone have any advice on where the heck I could possibly be going wrong?

Thanks in advance to anyone who can dig me out of this mess.

---

### Post by AJL on 2007-12-07
Dont forget to add this

> NameVirtualHost *:80

to your httpd.conf

---

