---
title: "Virtual vhost testing on host"
date: 2013-03-05
forum: Server Platforms
---

### Post by Rpgglitchy on 2013-03-05
Hello again Ubuntuforum!

Again, I am in trouble.. The issue that I have is that I have an apache server on a bladeserver that is meant for testing.
I am puzzling with the vhost configurations. in the /var/www/ I have created 3 drupal websites. They are currently running on [http://](http://)[IP address]/directory/
for each of the directories. That is not a problem. The problem is that I want to make them work when I enter [http://](http://)[directory]/
So I should make vhosts..

I installed webmin to have a nice webgui and easy configuration but I still have troubles making this work :/
the things I already have done/tried is creating copies from the /sites-available/default and renaming them to the sitename I want (let's call them site1.com and site2.com).
each containing Servername site1.com ServerAlias [www.site1.com]("http://www.site1.com") , ...
Then, I edited the hosts file in the webserver and added 127.0.0.1 site1.com,  127.0.0.1 site2.com.
ofcourse, when I try to type their names in my chrome browser on my host, this will not work. So I edited my windows hosts file [ip address server] site1.com

This would just send me to the index of my server.. That's not what I want and I cannot find a way to get redirected to the directories :/
Is there a kind soul out here that can aid me ? :D 

I thank you in advance, kind soul!

Greetings! :guitar:

---

### Post by GordThompson on 2013-03-05
1) When you cloned the 'default' file in /etc/apache2/sites-available and renamed the copies to 'site1.com' and 'site2.com' did you also change the ServerName, ServerAlias, and DocumentRoot directives in each of those files with the information for that particular site, e.g.,

```
ServerName site1.com
ServerAlias www.site1.com
DocumentRoot /var/www/directory1
```

2) After updating sites-available did you use the `a2ensite` command to enable the new sites you created? In other words, do you see corresponding symlinks when you do

```
ls -la /etc/apache2/sites-enabled
```

---

### Post by Rpgglitchy on 2013-03-09
Hi GordThompson,

Indeed, I did that. for both of them and enabled them. I think they would work if I would test them on a virtual linux client that is connected to that vswitch. but I am wondering if there is a way to test them from my host browser.

---

### Post by GordThompson on 2013-03-10
What does the following command display when you run it on the server?

```
sudo apache2ctl -S
```

---

### Post by Rpgglitchy on 2013-03-11
VirtualHost configuration:
wildcard NameVirtualHosts and _default_ servers:
*:80                   is a NameVirtualHost
         default server webserver1.stage.be (/etc/apache2/sites-enabled/000-default:1)
         port 80 namevhost webserver1.stage.be (/etc/apache2/sites-enabled/000-default:1)
         port 80 namevhost cega.stage.be (/etc/apache2/sites-enabled/cega.stage.be.conf:1)
Syntax OK

---

### Post by Rpgglitchy on 2013-03-11
I fixed it. the problem was in my /etc/hosts file in ubuntu itself ..  :/  misconfigured.
it had to be 127.0.0.1 with the servername from my new virtualhosts.

---

