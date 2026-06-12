---
title: "web server"
date: 2015-09-25
forum: Server Platforms
---

### Post by ackim on 2015-09-25
[COLOR=#000000][FONT=Times New Roman]The requested URL /joomla/ was not found on this server.[/FONT][/COLOR]
[HR][/HR]Apache/2.4.7 (Ubuntu) Server at 192.168.*.**Port 80

i am trying to install joomla on my ubuntu web server
but it giving the error on top
anyone can help me please?

---

### Post by QIII on 2015-09-25
Hello!

You should not be looking for /joomla in a URL. In fact, if you could get there something is seriously wrong with setup and security.  There shouldn't be any /joomla.

The link to my blog in my signature points to the URL theleftcoastgeek.net. That's the domain served by my VPS.  I have a LEMP server, so no Apache, but that doesn't matter.  That blog runs on Joomla.

Why are you looking for a URL containing /joomla in its path?

Addendum, now that I am at a PC instead of on my cell phone:

Joomla! is a content management/web page design toolset.  It's not part of the path to anything on your site.  If you are trying to complete the installation setup or modify the content and  layout of your site, you do that by going to mywebsite.whatever*/administrator*.  Don't use my blog as an example because if you try theleftcoastgeek.net/administrator, you'll get a 403 because I have Nginx configured to keep prying eyes out.

---

