---
title: "DAViCal Setup"
date: 2009-12-03
forum: Server Platforms
---

### Post by zigmo on 2009-12-03
I created a server to use for a DAViCal project I'm setting up. I've been following the directions [here]("http://ubuntuguide.org/wiki/DAViCal_tips") and so far everything was working fine. Now, when I try to access the server via a browser, I can only get the apache default, not the calendar interface.
I've tried accessing via hostname or direct IP address, but I can only access the root default page. I've read through the virtual hosts file, but neither the ServerName or ServerAlias will let me access my DAViCal setup.
I'm hoping this project will also teach me to work with apache (and DAViCal), but right mpw I'm completely lost as to why it isn't working.

---

### Post by volkswagner on 2009-12-03
Do you have any errors in /var/log/apache2/error.log ?

```
cat /var/log/apache2/error.log
```

You can try temporarily disabling the default vhost.  You may have a conflict using ports and non ports in the vhost file.

```
sudo a2dissite default
``` 

You can enable it again with

```
sudo a2ensite default
```

If the above does not give any leads, you may want to post your vhost file.

---

### Post by zigmo on 2009-12-07
I have a whole bunch of errors! I'm pretty sure my problem is that the DAViCal site is setup, but I'm missing some reference that let's me see it via a browser. I'm guessing the virtual hosts file I created isn't setup right. I copied it from the aforementioned site but, as I read through it, I couldn't find anything that seemed to point to the DAViCal directory I setup.
I tried your suggestions, but I got the same errors as before. Entering the site name just took me to the site and entering (what I thought) was the directory name just gave me a file not found.
I've attached my error log and my virtual hosts file from the sites-available directory (there is also a link to the sites-enabled directory pointing to the same file).
The site is on a computer on my work network and I can refer to it via either [http://ubuntu-server/](http://ubuntu-server/) or [http://ubuntu-server.local](http://ubuntu-server.local). The first is because I manually added it to our DNS and the second is because I was learning how to use zeroconf.

---

