---
title: "What Happened to Mediawiki"
date: 2016-06-24
forum: Ubuntu, Linux and OS Chat
---

### Post by DomIncollingo on 2016-06-24
Does anyone know why the mediawiki package was removed from 16.04?  Are there any plans to make it available again?  I store a lot of technical information on a mediawiki that I run locally, and it is no longer accessible since I upgraded from 14.10 to 16.04.  

I'm really rather upset about this.  It may be time to switch to a Mac.  The freedom and flexibility of Ubuntu are disappearing fast.:(

---

### Post by QDR06VV9 on 2016-06-24
Moved to Forum Feed Back

---

### Post by QIII on 2016-06-24
Not really FF&H either ...  :)

[This]("https://www.mediawiki.org/wiki/Manual:Running_MediaWiki_on_Ubuntu") might be of interest to you.  You can still install wikimedia.  You just have to do it manually.  

There are many, many possible reasons Canonical might choose not not include a package.  You might contact Canonical about that.

---

### Post by cariboo on 2016-06-24
This is probably a better sub-forum for this thread. 

I just installed mediawiki from the same place QIII linked to. I never had any luck installing it from the repositories, installing it manually worked the first time I installed it, and just I recently had to re-install it after upgrading to 16.04 server. The only extra configuration I had to was adjust the alias in /etc/apache2/sites-enabled/mediawiki.conf to reflect where I installed it.

```
cat mediawiki.conf
# Uncomment this to add an alias.
# This does not work properly with virtual hosts..
Alias /mediawiki /srv/www/html/wiki

<Directory /srv/www/html/wiki/>
	Options +FollowSymLinks
	AllowOverride All
	order allow,deny
	allow from all
</Directory>

# some directories must be protected
<Directory /srv/www/html/wiki/config>
	Options -FollowSymLinks
	AllowOverride None
</Directory>
<Directory /srv/www/html/wiki/upload>
	Options -FollowSymLinks
	AllowOverride None
</Directory>
```

---

### Post by QDR06VV9 on 2016-06-25
> This is probably a better sub-forum for this thread.
Thanks cariboo!:)

---

