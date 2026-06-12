---
title: "How to diagnose/fix massive first time byte?"
date: 2015-09-21
forum: Ubuntu, Linux and OS Chat
---

### Post by hopelessone on 2015-09-21
Hi,

[http://www.webpagetest.org/result/150921_H8_1DGN/1/details/](http://www.webpagetest.org/result/150921_H8_1DGN/1/details/)

the website first time byte loads in 10-12 seconds, it used to load in 0.5 seconds.

The problem started when the hosting company deleted the entire cPanel contents, after the restore the website was placed in a different folder and performed badly as you can see.

What should I start looking for in order to fix this?

Thanks,

---

### Post by tgalati4 on 2015-09-21
The website pings in 107 ms from NY to California, so that is OK.  That's perhaps the quickest you will ever get your page to respond.

Who is your hosting company?  They should be the ones helping you.  I don't see this as a linux or Ubuntu issue.

It's possible that your web root directory is misplaced and that is causing the server to peck through a large path statement to find your page elements.  But, the elements all seem to load quickly after the first byte, so perhaps it is a firewall or DNS problem from the hosting end.  Once the connection is established, the rest of the web page elements seem to load quickly.

---

### Post by hopelessone on 2015-09-21
Hi,

My hosting company was gadaddy, they won't help and just say it's a 'theme problem'. This only happened after they deleted my website, I had to pay a restore fee to get back cPanel, then we had to move everything manually across (godaddy did this), so thats what happened.

I ended up changing hostin companies and am hosting it now myself with a VPS, if I change theme it loads fast. So i know the issue resides in the theme..

I'm not sure where to look to fix this problem, as you say once you get the data, it loads real quick like it used to..

any ideas?

edit: i did find this weird one:
```
root@vultr:~# locate .htaccess
/var/www/html/wp-content/cache/zencache/cache/.htaccess
root@vultr:~# cd /var/www/html/wp-content/cache/zencache/cache/
root@vultr:/var/www/html/wp-content/cache/zencache/cache# ls -a
.  ..
```

locate .htaccess reports the file in that location, but when i look, there is nothing..weird?

---

### Post by hopelessone on 2015-09-22
fixed :) ended up being some old code inside the theme

---

