---
title: "Setting up Apache2"
date: 2007-02-16
forum: Server Platforms
---

### Post by colyn on 2007-02-16
I had a Windows 2k web server running Apache untill I upgraded to Ubuntu and have installed Apache2 on my Ubuntu 6.10 computer and have enabled port 80 in my router to the computers IP address. When I type in the IP address in my browser I see the default page so I know apache is running.

I have also placed my files in the /var/www folder.

How do I configure the server so others can access my website?

---

### Post by Flubs4u on 2007-02-16
I'd like to give this topic a bump because I'm experiencing something similar with a recent apache2 install on xubuntu.  
All the tutorials/walkthroughs/information i've read keeps talking about httpd.conf but the crazy thing is that my httpd.conf file is empty and it's contents seem to be in a file name apache2.conf.

---

### Post by conjur3r on 2007-02-16
> **Flubs4u said:**
> 
All the tutorials/walkthroughs/information i've read keeps talking about httpd.conf but the crazy thing is that my httpd.conf file is empty and it's contents seem to be in a file name apache2.conf.

That is most likely because the walkthroughs weren't made for Ubuntu.  The files you want to look at are: /etc/apache2/apache2.conf, /etc/apache2/sites-available/default, and probably /etc/apache2/ports.conf

Guys, if you can successfully look at your webserver from another machine on the network, then the problem is connectivity.  This may be due to incorrect port forwarding from your gateway/router to your server, or a firewall blocking the traffic.

Why I say this is the apache configs by default will serve all requests from any address to port 80.  If you've changed these directives, include it here.

---

### Post by Flubs4u on 2007-02-16
I figured everything out and now I can get to my server just fine.  Once I figured out that all my files need to go into /var/www everything is working just fine.

---

### Post by colyn on 2007-02-17
> **conjur3r said:**
> That is most likely because the walkthroughs weren't made for Ubuntu.  The files you want to look at are: /etc/apache2/apache2.conf, /etc/apache2/sites-available/default, and probably /etc/apache2/ports.conf

Guys, if you can successfully look at your webserver from another machine on the network, then the problem is connectivity.  This may be due to incorrect port forwarding from your gateway/router to your server, or a firewall blocking the traffic.

Why I say this is the apache configs by default will serve all requests from any address to port 80.  If you've changed these directives, include it here.

My problem is how to configure apache to show the web pages. When I type in my url I get a page Index of/ with a folder apache2-default/ (link) 

Next line reads Apache/2.0.55 (Ubuntu) Server at colyngoodson.com Port 80

If I click on the "apache2-default" link it then goes to the index.html file

How do I configure it to go directly to the index.html file instead of the above default??

---

### Post by colyn on 2007-02-17
> **colyn said:**
> My problem is how to configure apache to show the web pages. When I type in my url I get a page Index of/ with a folder apache2-default/ (link) 

Next line reads Apache/2.0.55 (Ubuntu) Server at colyngoodson.com Port 80

If I click on the "apache2-default" link it then goes to the index.html file

How do I configure it to go directly to the index.html file instead of the above default??

I got the server up and running finally but was wondering how to clear the access and error log files??

I prefer to clear the log files once a month..

---

### Post by MJN on 2007-02-17
Change the configuration in **/etc/logrotate.d/apache2** to suit (use **man logrotate** as your guide).

Mathew

---

