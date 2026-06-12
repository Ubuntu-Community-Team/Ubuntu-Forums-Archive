---
title: "How do you deny access to a website folder or files?"
date: 2007-09-03
forum: The Cafe
---

### Post by user1397 on 2007-09-03
How can you do it so that people get a "Access Denied" sort of message if they try to go to your website files dir?  

I imagine this is used so that no one steals your code, and even though I'm all pro-open source, this would be part of a website-redesign project I'm working on for a company, and they want this feature.

---

### Post by user1397 on 2007-09-03
bump

---

### Post by HermanAB on 2007-09-03
You configure it in /etc/httpd/conf/httpd.conf with deny and allow rules for each virtual host on your server.  This gives you very fine grained control.

Go to the Samba web site and start reading.  This is not a simple question, since there are various ways to do it.

Cheers,

H.

---

### Post by user1397 on 2007-09-03
> **HermanAB said:**
> You configure it in /etc/httpd/conf/httpd.conf with deny and allow rules for each virtual host on your server.  This gives you very fine grained control.

Go to the Samba web site and start reading.  This is not a simple question, since there are various ways to do it.

Cheers,

H.ah i thought it would just be some code you could put in your website (i don't have access to the company's web server right now, and the site doesn't use php or anything, it's just n information site (xhtml and some javascript)

also just so so understand, i am not working on linux right now, I'm actually doing most of my web designing on windows

thanks for replying

---

### Post by popch on 2007-09-03
> **HermanAB said:**
> You configure it in /etc/httpd/conf/httpd.conf with deny and allow rules for each virtual host on your server.  This gives you very fine grained control.

Go to the Samba web site and start reading.  This is not a simple question, since there are various ways to do it.

Cheers,

H.

Actually, you should not read the documentation on ***Samba ***but on the ***web server*** being used. 

Some web server (e.g. Apache) can be so configured that the access rights and other parameters can be set individually per directory.

---

### Post by st4rdr1ft3r on 2007-09-03
Or you could chmod 640 the files/dirs you want to protect

---

### Post by userundefine on 2007-09-03
htaccess

---

### Post by user1397 on 2007-09-03
okay I guess I thought it was easier than editing web server config files, thanks for all the replies.

---

### Post by Sporkman on 2007-09-03
You could also give the directory a cryptic name.

---

