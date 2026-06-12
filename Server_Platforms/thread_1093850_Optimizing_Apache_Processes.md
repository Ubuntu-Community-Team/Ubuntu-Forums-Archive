---
title: "Optimizing Apache Processes"
date: 2009-03-12
forum: Server Platforms
---

### Post by firefly2442 on 2009-03-12
I setup MySQL, Apache2, and PHP5 on my Asus eeePC.  I tuned apache2.conf by doing the following:

> 
<IfModule mpm_prefork_module>
StartServers 1 //default was 5
MinSpareServers 1 //default was 5
MaxSpareServers 10
MaxClients 150
MaxRequestsPerChild 0
</IfModule>


Essentially, I am the only one going to be accessing the server to do some light development work on the road.  Are there other things I should do to optimize Apache on my limited hardware?  Are there other things that I can do to optimize MySQL or PHP?  I noticed the MySQL server takes up quite a bit in terms of RAM.

Thanks in advance. :)

---

### Post by mrsteveman1 on 2009-03-12
Yes you can edit /etc/mysql/my.cnf and change some of the variables, on some distros there are commented out sections for large or small servers, but i do believe that Sun has documentation available on their site as to what each item does and what would be best for a very small server.

---

