---
title: "Virtual servers with Apache"
date: 2010-01-12
forum: Server Platforms
---

### Post by djanie78 on 2010-01-12
I need help fellas.
Virtual servers, apache2, webmin.

Right I got two sites in two different directories on my server. The idea is to map them to two different hostnames. Both on http port 80.

xxx.com will go to /www/xxx/index.htm
yyy.com will go to /www/yyy/index.htm

using webmin, i create a virtual server or shall i say two virtual servers and map them. Is it that straight forward?

Someone help please?

---

### Post by R.Bucky on 2010-01-13
Do you mean Virtual hosting? You will need a static ip. Follow this post [http://buckycomputing.net/blog/hosting-2-domains-with-1-server/]("http://buckycomputing.net/blog/hosting-2-domains-with-1-server/")

---

### Post by neoanderthal on 2010-01-14
If your DNS entries for xxx.com and yyy.com are configured correctly, I believe it will work in the fashion you want. I don't know about using webmin, but Apache's documents on virtual hosts can be found here:
[http://httpd.apache.org/docs/2.0/vhosts/examples.html](http://httpd.apache.org/docs/2.0/vhosts/examples.html)

---

### Post by tlsarles on 2010-01-14
What you want isn't too hard. As I think others have eluded too, your DNS provider should be mapped so that this.com and that.com both point to the IP of the server that will be hosting the two domains. Then you just gotta do the Apache config.

Ok, so your main apache2.conf you don't usually need to touch. instead, go into /etc/apache2/sites-available/

in that folder, you will need to create a config file for each vHost. so create /etc/apache2/sites-available/this

```

<VirtualHost *:80>
   ServerName this.com
   DocumentRoot /var/www/this/
</VirtualHost>

```

And make a config file for that.com, with the same syntax.

now you just need to enable the site so do a 

```
a2ensite this
```

and restart apache

```
/etc/init.d/apache2 restart
```

The End

---

### Post by djanie78 on 2010-01-16
> **tlsarles said:**
> What you want isn't too hard. As I think others have eluded too, your DNS provider should be mapped so that this.com and that.com both point to the IP of the server that will be hosting the two domains. Then you just gotta do the Apache config.

Ok, so your main apache2.conf you don't usually need to touch. instead, go into /etc/apache2/sites-available/

in that folder, you will need to create a config file for each vHost. so create /etc/apache2/sites-available/this

```

<VirtualHost *:80>
   ServerName this.com
   DocumentRoot /var/www/this/
</VirtualHost>

```

And make a config file for that.com, with the same syntax.

now you just need to enable the site so do a 

```
a2ensite this
```

and restart apache

```
/etc/init.d/apache2 restart
```

The End

Thank you all for your help. Sorted with the instructions quoted above. You my friend are a star. 
Now how do i disable a site i.e the opposite of *a2ensite this*

---

### Post by neoanderthal on 2010-01-16
my enabled sites are symbolic links to the configuration files in /etc/apache2/sites-available - i just remove the symlink in sites-enabled that points to the configuration file for the site I wish to disable, and restart apache.

the companion to a2ensite is a2dissite, which is a script that does this automatically.

man a2ensite for more information :)

---

### Post by jocampo on 2010-01-16
neo,

I faced a similar issue months ago. I was able to install two sites with 1 IP. Take a look on this thread that I created.

[http://ubuntuforums.org/showthread.php?t=1249354]("http://ubuntuforums.org/showthread.php?t=1249354")

---

### Post by djanie78 on 2010-01-18
OK that was me bieng a ****. Forgot all about the man command. All works good though guys. Thanks you all very much

---

### Post by tlsarles on 2010-01-18
a2dissite or something like that......

---

### Post by Sporkman on 2010-01-18
> **tlsarles said:**
> now you just need to enable the site so do a 

```
a2ensite this
```


I usually just make a link in sites-enabled (with an appropriately-numbers xxx- prefix).

---

### Post by vamega on 2010-01-19
[@ djanie78]("http://ubuntuforums.org/member.php?u=698090")
djanie78, that was very useful to me, I've been wanting to do exactly this, and your advice made it extremely simple.

I wanted to tell you that I'm compiling a How-To on my website, and that I'm going to include a slightly modified version of what you said on it. I hope you don't have any objections, I will of course link to this forum post, and credit you appropriately.

Vamega

---

