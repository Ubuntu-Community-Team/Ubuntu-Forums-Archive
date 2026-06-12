---
title: "Help setting up ubuntu server ed."
date: 2009-02-03
forum: Server Platforms
---

### Post by black445 on 2009-02-03
Hello, 

I had recently set up an old computer, and installed ubuntu server ed. on it, plugged it into my router, and I have LAMP installed as well.

I really don't know where to go from there, I would like my server to host websites, that's it really.  I also have my main PC connected to the same internet network. 

How would i go about getting my web pages (created in XHTML, CSS) onto the server so it can be seen online by everyone?  

Thanks in advance :)

---

### Post by Rhiknow on 2009-02-03
> **black445 said:**
> Hello, 

I had recently set up an old computer, and installed ubuntu server ed. on it, plugged it into my router, and I have LAMP installed as well.

I really don't know where to go from there, I would like my server to host websites, that's it really.  I also have my main PC connected to the same internet network. 

How would i go about getting my web pages (created in XHTML, CSS) onto the server so it can be seen online by everyone?  

Thanks in advance :)

Basically:

Install Apache2. (sudo apt-get install apache2). Start the Apache2 server using sudo apache2ctl start

Put your html in /var/www

view the html by typing into another computer terminal's internet browser:
[http://ppp.qqq.rrr.sss/](http://ppp.qqq.rrr.sss/)
, where ppp.qqq.rrr.sss is the server's IP address

If you want to serve php pages: sudo apt-get install php5

---

### Post by Iowan on 2009-02-03
To be visible on Internet, you'll need a static IP Address from your ISP, or a service like **no-ip** (or dyndns?). You will need to set up your router to port-forward to your server.

If you installed LAMP, PHP5 *should* already be installed. The default place for files is (as mentioned) /var/www, but you can put them in a more convenient place, if you wish.  [Here]("https://help.ubuntu.com/community/ApacheMySQLPHP") is a good starting point, but you should also carefully consider security.

---

### Post by skunkbad on 2009-02-03
> **Iowan said:**
> ... or a service like **no-ip** (or dyndns?). ...

I like zoneedit. I run a webserver with 4 sites on it, and zoneedit combined with ddclient keeps them available 24/7.

---

