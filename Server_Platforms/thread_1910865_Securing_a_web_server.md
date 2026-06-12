---
title: "Securing a web server"
date: 2012-01-17
forum: Server Platforms
---

### Post by ScottG89 on 2012-01-17
I was wondering what options I should enable/disable in my apache and/or php/mysql config. Also tips on editing iptables and any other security actions I should think about before putting my web server up (I can't find a good web hosting company).

Thank you,
Scott G

---

### Post by Habitual on 2012-01-18
.htaccess

Deny from all
Allow from your_ip

---

### Post by hackertarget on 2012-01-18
Install ossec.net, plenty of good documentation around covering the install and tuning.

It is an excellent way to monitor a web server for security (and system) issues. There is also an optional active response mode that can do blocking.

---

### Post by TwiceOver on 2012-01-18
Just one thing...  If you are going to install phpmyadmin then put the whole folder behind an .htaccess username/password prompt.  This of course causes a double logon but is more secure than just the phpmyadmin login which gets hacked regularly.

---

### Post by Dangertux on 2012-01-18
Seriously, if you're going to be hosting any type of web application other than just a static page, anything that takes user input at any point. You really need a web application firewall. I highly recommend Mod-security if you're using Apache. 

I wrote a guide on that a while back here : [http://dangertux.wordpress.com/tutorials/ubuntu-10-04-apache-current-mod-security/](http://dangertux.wordpress.com/tutorials/ubuntu-10-04-apache-current-mod-security/)

Also OSSEC is good, but well, HIDS has it's issues. For one IDS in general is usually very easy to creep past. Overall you need to focus most on the following areas for a web server.

- Harden services : Run strong configurations, some people already touched on .htaccess, but there are other things, disable unsafe options, TRACE being one. Avoid directory listing etc. You can google for decent configs. Keep your services upgraded. Also don't fall into the FTP trap unless you have to , use SFTP if possible, if you HAVE to use FTP I suggest spending a LOT of time configuring your FTP service. Strong credentials regardless of which you use, etc.

- GOOD CODE : If you're writing your own web application or using someone elses make sure it's well coded, in the event it's not and doesn't sanitize input, this is what you're web application firewall is for.

- Permissions : Get them right, keep them right, a lot of web apps want 777 on everything they touch, this is stupid come up with the work arounds, least permissions for the job etc.


If you're using a database backend that's hosted on the same server you could also consider a DBMS firewall like green sql or something of that sort as well.

Hope this helps.

---

