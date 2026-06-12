---
title: "/avr/www ??"
date: 2007-07-21
forum: Server Platforms
---

### Post by nlbs on 2007-07-21
I've just Installed apache2 
yes the Document root is pointed towards towards /var/www
**But why the httpd.conf file is Blank**
and in apache2.conf its
ServerRoot "/etc/apache2"
but where is the 
DocumentRoot "/var/www"
**If there is no DocumentRoot why Its pointing towards /var/www**

---

### Post by nlbs on 2007-07-21
Aha!
I've just Found that
there is /etc/apache2/sites-available/default
That does it
Is it a recent change in Apache2 
??

---

### Post by p_quarles on 2007-07-21
I'm not completely sure I understand your question, but here's the answer to what I think you're asking.

The Debian configuration of Apache is kinda strange. apache2.conf is the main configuration file, and httpd.conf is left blank for user customizations. That file, as well as a few others, are linked by the "Include" directives in apache2.conf. If you look at all the the files linked by Include, you'll probably find one that points the document root to /var/www. 

That said, the wonkiness of the Debian configuration is exactly why I got rid of it and installed the latest version from source.

---

