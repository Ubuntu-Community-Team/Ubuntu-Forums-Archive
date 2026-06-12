---
title: "accessing to DB systems installed in 2 servers"
date: 2012-11-05
forum: Server Platforms
---

### Post by herbert tamayo on 2012-11-05
Hi, I have one single public IP, I have a Database System that is published in the web using this public Ip in a pc that I call server1. Now I need to publish in the web additional software, these software will be installed and running in server2. all software, server1 and server2, are LAMP based - Linux Ubuntu+Apache+MySQL+PHP- , my questions are:

1. How Can I publish in the web the software installed in server 1 and server 2 and that they can be accesible through my one single public ip?

2. Virtualization is not an option, because my hardware specs are not the best to do it that way, the software installed in server 1 is very important, the software that will be in server 2 is a complement, for example helpdesk, all same users can access to any software, each software has login form, the server1 will act as a gateway for server2 software?

3. the fact that all systems will be accesible from the same ip public, does this fact will impact in any server1/server2 performance? 

4. what is the best way to publish all service using just one single public ip and two servers?

Thanks for your answers

Regards

Herbert

---

### Post by dannyboy79 on 2012-11-05
if you only have a consumer level router I am not sure how you would accomplish this because you can only forward port 80 to one internal IP address. Y can you just run all the software on 1 server?

---

### Post by herbert tamayo on 2012-11-06
in fact we have a good firewall, cisco routers, layer 3 switches all some kind of network stuff, in fact the network administrator is kind of lazy, i had more than a month with this problem and I'm decided to solve this, in networking I'm basic so I'm not clear what is the best way, in fact i don't have any idea. Also i can run all software from server 1, that is because the server 1 has mission critical data, the server 2 would have support software, for example helpdesk, e-learning platform, development environment, etc.

a good help would be what topics should I check/learn to solve this, someone may suggest something?

regards

---

### Post by SeijiSensei on 2012-11-06
Just use [name-based virtual hosting]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html").  That enables Apache to serve different content depending on the host name that appears in the URL.

In Ubuntu, all the virtual host specifications are placed in /etc/apache2/sites-available with symlinks to these files in /etc/apache2/sites-enabled.  (The a2ensite command creates these links, or you can do it yourself.)  Clone the file /etc/apache2/sites-enabled/default and replace the Apache directives with ones appropriate to you sites.  See the [Ubuntu Server Guide](https://help.ubuntu.com/12.04/serverguide/httpd.html) for more details.

---

