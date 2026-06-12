---
title: "Custom 404 page troubleshooting, creating a good apache2.conf"
date: 2006-09-15
forum: Server Platforms
---

### Post by capsid on 2006-09-15
i know that people have asked before about creating a custom 404 page, but I think i'm asking about it in a slightly different context.  I just got my first webserver up (apache2, php5, mysql5, according to the unofficial ubuntu starter guide. ) and I needed to make a 404 page to keep it from blabbing about my OS and what kind of server I use when someone requests a nonexistant page.  So I edited my apache2.conf like so:
    
> ...
ErrorDocument 404 [http://mywebpage.com/404.html](http://mywebpage.com/404.html)
...


and I put the 404 page in /var/www/404.html .

Even though I've tried a couple of things and restarted the server a bunch of times, it's still giving the default error page.  I tried to open up the original HTTP_PAGE_NOT_FOUND.html.var, but I guess it's not a text file?

So I came on here and searched, and I haven't found many suggestions beyond changing what I've already changed and restarting the server, but I did find this thread:
[http://ubuntuforums.org/showthread.php?t=163599&highlight=cross+site+scripting](http://ubuntuforums.org/showthread.php?t=163599&highlight=cross+site+scripting)
about a few rules that prevent against cross-side scripting. 

So i'm wondering if anybody can help me figure out why my edit in  apache2.conf isn't working, and possibly post a well-crafted apache2.conf that contains some other tweaks for hotrodding the default ubuntu package installation.   

Thanks a bunch.

---

### Post by capsid on 2006-09-15
ok, so I got the 404 working, but I'm still interested in any advice for making a more secure apache2.conf.

---

### Post by Hadron Quark on 2006-09-16
if you're going to ask questions at least post how you got it working for other people to google up!

thanks :)

---

