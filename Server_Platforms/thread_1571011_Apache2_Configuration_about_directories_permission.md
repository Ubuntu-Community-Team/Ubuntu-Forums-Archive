---
title: "Apache2 Configuration about directories permission"
date: 2010-09-09
forum: Server Platforms
---

### Post by r3nfr3w on 2010-09-09
Hi,

Recently, I had this idea of coding my own web UI for my media center to learn PHP and Apache.

My architecture is quite simple. I have my website in /var/www and all my media on another hd in /media/otherhd.

What I am trying to do, for quite some hours, is to access all my media from apache2.

I know it is about directives in the configuration file of apache2 so I decided to write my modifications in the file /etc/apache2/conf.d/security

After some readings on apache configuration on ubuntu, the configuration file doesn't really matter because they are all included in the main one apache2.conf. (Correct me if I'm wrong)

Unfortunately, this is were everything gets complicated, I haven't found on the web a good tutorial for noobies about the <directory> directive. After reading apache core features I came out with this and it is an epic fail.


```

#this is to protect file systems
<Directory />
	AllowOverride None
	Order Deny,Allow
	Deny from all
</Directory>

#overriding because I want this directory to be accessible rwx
<Directory /media/otherhd/>
	AllowOverride All
</Directory>

```

All I want is to get access (read, write, execute) with my php code to this directory
/media/otherhd without compromising security on my server.

What should I write then?

Thanks in advance for any help,
r3n

---

