---
title: "Ubuntu Desktop Server, Joomla, Changing IP to URL HELP!"
date: 2010-12-23
forum: Server Platforms
---

### Post by bloodhacker2 on 2010-12-23
Ok guys this is what i got going on. I am running ubuntu 10.04 server with desktop and with the latest edition of joomla loaded on it.

I have fully installed and configured joomla with no problems.

Right now to get to my sight i put in the IP of the server into my browser and i can view my site and make changes anywhere i want.

like this [http://100.100.100.100/Joomla/](http://100.100.100.100/Joomla/) ( This is not my real ip just an example)

I have gone to register.com and have set my "A" record for my url to point to that IP.

The problem is that i forgot which file it is to configure the settings so that when someone types in my URL it points them to my Joomla file/site

Any help would be great!

---

### Post by CharlesA on 2010-12-23
You'd have to tell Apache that /path/to/Joomla is the DocumentRoot.

You basically have to set up a virtualhost, and the file you would edit is /etc/apache2/httpd.conf

---

### Post by bloodhacker2 on 2010-12-24
So i went to the httpd.conf file and found that their was nothing in it to edit. So i went to etc/apache2/sites.available and went to the document default and edited the path directory to my Joomla site and now everything seems to be working. 

Was this a good ideal to do?

---

### Post by CharlesA on 2010-12-24
That would work too.

I normally just set up a virtualhost like this:

```
charles@lucid:~$ cat /etc/apache2/httpd.conf
<VirtualHost *:80>
DocumentRoot /home/charles/site/
</VirtualHost>

```

But then, I'm lazy.. so.. yeah. :P

---

