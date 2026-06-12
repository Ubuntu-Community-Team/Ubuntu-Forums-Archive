---
title: "lighttpd don't work on liveCD ?"
date: 2009-04-18
forum: Server Platforms
---

### Post by FAo10rK on 2009-04-18
I try to use lighttp on a liveCD (based on xubuntu 8.04) and I can't see the index.html page.

I tried to use apache with the bug ([http://ubuntuforums.org/showthread.php?t=616720](http://ubuntuforums.org/showthread.php?t=616720)) on unionFS, correct my apache2.conf and I can see my index.html page.
(EnableSendfile Off)

But if if I try with the lighttpd, I just see a blanck page on [http://localhost/index.html](http://localhost/index.html)
I don't have modify the /etc/lighttpd/lighttpd.conf
root document are on /var/www
and index-file.names content index.html

Do you have the same problem ?

Are there others lights web servers on Ubuntu just for index.html pages ?

---

### Post by BkkBonanza on 2009-04-18
**Nginx** is in the Ubuntu repository and it's as light/lighter than lighttpd. It's also generally favoured over lighttpd now due to memory leak issues and lack of ongoing activity in lighttpd. I use nginx for quite a few web sites and would highly recommend it. They have a very active mailing list where you can talk with the people actively developing it. It's used by some big name sites too.

See [http://wiki.nginx.org//Main](http://wiki.nginx.org//Main)

BTW I haven't used either of these from the livecd and don't know if there are problems with that.

---

### Post by FAo10rK on 2009-04-18
I just try it on a livecd and the problem is the same.

I can't see a simple HTML page with nginx.

The webserver is started but the web page index.html on /var/www is blank.
I try to modify the option Sendfile to Off, but it doesn't work.

Another idea ?

---

### Post by BkkBonanza on 2009-04-19
It doesn't sound like a problem with the webserver but with the persistence config for the livecd. I'm not familiar with that but I'm sure somewhere around here there is a tutorial on how to enable persistence when using the livecd. It has to be able to save it's changes.

I'm not sure what you mean by the "option Sendfile". I would think the next step is to read over the docs and check again any confiuration settings. I don't think there's any reason that it shouldn't work though. If you are getting a valid page back - no error - then the server must be running ok and the problem is with configuration as to where it's getting the default html file. Probably something real basic - it always is.

---

### Post by FAo10rK on 2009-04-19
No, I already use the persistence in the liveCD  and it's not the problem here. I don't want to save my docs or my configuration, just use a wbeserver on a liveCD.

Just try it :
Launch a livecd, install a webserver and try to see a simple web page with lighttpd or nginx. It works with apache with a small page, but if your page is longer, your page won't be seen.


I found the solution with lighttpd :
[http://redmine.lighttpd.net/issues/471](http://redmine.lighttpd.net/issues/471)

I add this line in the /etc/lighttpd/lighttpd.conf :
```
server.network-backend = "writev" 
```

And it works !

Thanks.

---

