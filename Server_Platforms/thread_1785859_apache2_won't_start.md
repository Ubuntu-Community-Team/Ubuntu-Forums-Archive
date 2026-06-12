---
title: "apache2 won't start"
date: 2011-06-18
forum: Server Platforms
---

### Post by Jugg on 2011-06-18
I am trying to set up a personal web server. I have ubuntu 10.04.
I followed the directions listed here to try and install apache2 but after I run:
```
sudo /etc/init.d/apache2 restart
```
I get the message:
```
*Restarting web server apache2                   [fail]
```
and I can't view my site. Does anyone know how to fix this?

---

### Post by craigcrawford114 on 2011-06-19
Check the apache2 log, it will most likely tell you what is going wrong.

---

### Post by Jugg on 2011-06-19
thanks for the help, I had changed the location of the logs but forgot to create the new directory

---

### Post by Jugg on 2011-06-19
one more thing, when i try to view the page, neither css or the js files are being read. Do you know how i can fix this?

---

### Post by craigcrawford114 on 2011-06-19
> **Jugg said:**
> one more thing, when i try to view the page, neither css or the js files are being read. Do you know how i can fix this?

CSS and JS files are processed by the client, they are passed to the client just like any other HTML data. Check the apache2 log and if you see nothing in there then it might be a client issue.

---

### Post by Jugg on 2011-06-19
The log says that permission to the directory where I have my css and js files was denied. How can I allow access to these directories?

---

### Post by crispy_420 on 2011-06-22
I'm no pro with apache but couldn't you open the directory up with read/execute for all until you research more?

---

