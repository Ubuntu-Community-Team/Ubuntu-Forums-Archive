---
title: "Setting up URL redirect (LAMP - - 14.04)"
date: 2017-01-23
forum: Server Platforms
---

### Post by Drone4four on 2017-01-23
I&#8217;m trying to do a URL redirect for my humble DigitalOcean droplet (LAMP stack). The O/S version I have running is Ubuntu 14.04 and the Apache version I am running is 2.4.7.

I have a web page buried in six or seven sub directories below my public_html homepage.  My destination looks something like this:

```
www.mydomain.com/portal/essays/subDIR1/subDIR2/greg/index.html
```

I wish to create a link so that when I give a visitor this link here:

```
www.mydomain.com/greg
```

...it automatically takes them to the first link, at the buried web page.
		
So I Google &#8216;digitalocean url redirect&#8217; which takes me to [a helpful tutorial for Apache]("https://www.digitalocean.com/community/tutorials/how-to-create-temporary-and-permanent-redirects-with-apache-and-nginx"). Here I learned that if I want to direct visitors away from my homepage to a homepage on a different domain, this is the example code I have to add to my /etc/apache2/sites-available/site.com.conf:
```

<VirtualHost *:80>
        ServerName www.domain1.com
        Redirect / http://www.domain2.com
</VirtualHost>

```

So I tried adding this to my config file:
```

	ServerName www.mydomain.com
	Redirect www.mydomain.com/portal/essays/subDIR1/subDIR2/greg/ www.mydomain.com/greg

```
When I restart Apache, the prompt returns this:
```

 * Restarting web server apache2                                         [fail] 
 * The apache2 configtest failed.
Output of config test was:
AH00526: Syntax error on line 29 of /etc/apache2/sites-enabled/summitministry.conf:
Redirect to non-URL
Action 'configtest' failed.

```
Line 29 = ```
Redirect www.mydomain.com/portal/essays/subDIR1/subDIR2/greg/ www.mydomain.com/greg
```
I&#8217;m evidently doing something wrong.  I have a hunch that this DigitalOcean doc isn&#8217;t really where I need to be because I do not have a second domain.  I only have the one.

That DigitalOcean doc also explains redirect 301&#8217;s which when I Google that, it takes me to a helpful Google support document which includes [a terrific YouTube video]("https://www.youtube.com/watch?v=r1lVPrYoBkA"). But again, this explains how to redirect to a different domain, which isn&#8217;t what I need at all.  

Can someone please recommend some other Google search terms to help me achieve what I have set out to achieve?

---

### Post by SeijiSensei on 2017-01-24
A redirect just points to another root URL, not a page.  You need to use an "[alias]("https://httpd.apache.org/docs/current/mod/mod_alias.html")".

```

<VirtualHost *:80>
ServerName www.example.com
Alias /greg /path/to/portal/essays/subDIR1/subDIR2/greg
<Directory "/path/to/portal/essays/subDIR1/subDIR2/greg">
[options like these if appropriate]
    Options +Indexes
    AllowOverride All
</Directory>
</VirtualHost>

```

Now [http://www.example.com/greg](http://www.example.com/greg) will point to the directory you want.

---

### Post by mastablasta on 2017-01-24
also when dealing with apache - they really have good documentation along with examples and explanation. no reason not to use it.

---

