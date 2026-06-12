---
title: "[SOLVED] httpd.conf settings"
date: 2008-07-19
forum: Server Platforms
---

### Post by sp0nge on 2008-07-19
Hello, 

I'm working to set up my first server to experiment hosting my own web pages. I have installed Ubuntu 8.04 server and have downloaded and attempted to install ISPConfig control panel. Upon installing, I get an error message: 

```
Checking for program httpd...
/usr/bin/httpd
OK
Checking the syntax of the httpd.conf...
httpd: bad user name ${APACHE_RUN_USER}
ERROR: The syntax of your httpd.conf is not ok! Please correct the error. The in
stallation routine stops here!
```

Upon viewing /etc/httpd/conf/httpd.conf I see there is nothing in the file. Is there a recomendation on how to set up this config file? I have seen a few basic examples but I want to use the best config for Ubuntu.

---

### Post by mbeach on 2008-07-19
you can look in /etc/apache2/ for the defaults as given by the Ubuntu package.  If its just for your own web pages, you may not need all that ISPConfig is giving you.  Install apache2 from Synaptic - get a feel for it, then if you need some the extras that ISPConfig offers, use them, but after you've already gotton the basics of Apache down.  I find that installing more complicated apps than you need right out of the gate makes it a steeper learning curve than need be.  Also, most folks here are familar with the default setup/file locations etc, but I'd bet ISPConfig has its own defaults which many folks in these forums will not be as familiar with, thus making it more difficult to provide easy support.

---

### Post by sp0nge on 2008-07-19
Good advice, thank you. 

I'll hold off pursuing ISPConfig. It seems helpful, but I'm all for the philosophy of walking before you run.

Out of curiosity, I tried to view /etc/apache2/httpd.conf and there was no data in the file. Am I missing something?

---

### Post by mbeach on 2008-07-19
look for most stuff in 
/etc/apache2/apache2.conf  (more global type stuff for the server)

some other stuff in:
/etc/apache2/conf.d
/etc/apache2/ports.conf
/etc/apache2/sites-available/default  (specific to a default site instance)

good luck.
mb

---

### Post by sp0nge on 2008-07-21
So I thought this was unnecessary, but I have found a project that leads me to change the document root by editing the directory in httpd.conf. 

I started poking around and finally found httpd.conf, but when I go to open it, there is NOTHING THERE!> The guide I'm following is geared towards windows servers, so I'm transposing a lot of information in my head on the fly. I suppose this step is not necessary, as apache is displaying the web pages loaded into /var/www, but I would like to understand what I'm missing. 

Shouldn't this file come with some sort of pre-config?

---

