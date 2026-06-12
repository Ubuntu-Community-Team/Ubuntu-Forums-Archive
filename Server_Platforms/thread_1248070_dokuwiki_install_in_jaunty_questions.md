---
title: "dokuwiki install in jaunty questions"
date: 2009-08-23
forum: Server Platforms
---

### Post by juicymixx on 2009-08-23
Hey,

I'm working on a new install of Jaunty, and I just installed LAMP everything using the defaults.   I then wanted to install dokuwiki, and was pleasantly surprised that it could be done through the graphical synaptic package manager - so I went ahead and did it.   Well, now I'm a bit confused, because while the Apache2 install seems to work well, I can't figure out where dokuwiki installed itself, and how to access it through any web interface.   Anyone have any clues?   Ideally I had wanted to install dokuwiki into ~specificuser/public-html/dokuwiki but right now I'm just not even sure where synaptic has installed it.

thanks.

---

### Post by cariboo on 2009-08-23
THe way dokuwiki is setup by default is that it can only be accessed from 127.0.0.1, you need to change the apache.conf file to allow access from other computers. to do this change the following line:

```
<Directory /usr/share/dokuwiki/>
	Options +FollowSymLinks
	AllowOverride All
	order allow,deny
	**allow from 127.0.0.1**
</Directory>
```

to **allow from all**

Restart apache2:

```
sudo /etc/init.d/apache2 restart
```

After the restart you should be able to access the wiki.

---

