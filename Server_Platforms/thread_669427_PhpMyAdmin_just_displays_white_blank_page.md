---
title: "PhpMyAdmin just displays white blank page"
date: 2008-01-16
forum: Server Platforms
---

### Post by trymbill on 2008-01-16
I had phpMyAdmin running before I almost destroyed my Ubuntu Server later today.  I was just messing with it and somehow got Apache2 to display an error on every page I tried to open.

I got that fixed simply by removing apache2 and php5.

Now, I have a symlink from /var/www/phpmyadmin to /usr/share/phpmyadmin and that works great.  When I open [http://localhost/phpmyadmin](http://localhost/phpmyadmin) it shows me the login page for phpmyadmin.  But when I log in and it tries to display the 2-framed page with all the information, I just get a blank white screen in Firefox.  Internet Explorer says "Can't display this page" and if I look at the source code there is nothing more than the normal html, header, title, body and then the frame code but nothing inside the frames.

This is strange because I had the same problem with the website I'm running on this server but that got fixed in all the "fixing" I had to do earlier but phpmyadmin seems to be left behind.

I tried removing phpmyadmin and setting it up again but that didn't work.  I looked over the the error.log and access.log for apache2 and they don't show anything strange.  I'm quite lost here :-/

Do I need to post some other info here for you to help me?  Please let me know.

Sincerely,
Magnus

---

### Post by trymbill on 2008-01-17
This is just a bump ...

---

### Post by trymbill on 2008-01-18
I think I'm getting closer to the answer here ...

... when I try to restart or force-reload my Apache2 I get a "Segmentation Fault" error and I can't restart or force-reload my server.  I tried Googling "Segmentation Fault Apache2" and I mostly got something related to PHPmyadmin.  So I tried uninstalling with apt-get:

```
apt-get remove phpmyadmin
```

But I still get the segmentation fault.  I don't see the error in my error.log and I don't know if i uninstalled phpmyadmin correctly.

Can someone point me in the right direction here please? :)

---

