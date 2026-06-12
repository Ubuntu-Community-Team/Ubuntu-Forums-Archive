---
title: "Hosting two sites on Ubuntu Server"
date: 2008-09-20
forum: Server Platforms
---

### Post by rwslippey on 2008-09-20
Hello everyone... I have a situation hopfully someone can help...

I have a need to host two websites ... these sites are going to be completly seperate from one another.. (except on the same server and using the same IP address) 

Trouble is I have a dynamic IP and my ISP blocks port 80...

I am hosting one site using a DNS server (no-IP) witch just redirects to my IP address .... whatever it is at that time. 

How would this play with hosting two sites on one. Would their be a way for the server to distinguish between witch one the client was requesting. 

I was thinking of using different ports for each seperate domain....   any ideas...

thanks again


rob

---

### Post by mbeach on 2008-09-20
you don't need different ports.  You want to be looking into virtual host files (located in /etc/apache2/sites-available).  Copy the default, then adjust accordingly for your second site.  The ServerName directive controls how apache handles which site is being requested.  For your local testing edit your /etc/hosts file to point your 'domain' (which will be same as your ServerName in the virtual host file) to your ubuntu server's ip address (if testing from the browser on the same machine use the 127.....)

---

