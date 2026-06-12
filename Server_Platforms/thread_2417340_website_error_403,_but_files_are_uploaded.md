---
title: "website error 403, but files are uploaded"
date: 2019-04-22
forum: Server Platforms
---

### Post by tomdf on 2019-04-22
Hi Guys,

i am running ubuntu 18.04 and ISPConfig 3.0 with apache 2 

I uploaded wordpress backup to the server.
When i make ls /var/www/clients/client1/web5/web I can see all the files on the server. 
When i want to see the file in the browser i get a forbidden 403 that the files does not exist.

for example: teneriffa-akupunktur.com/installer.php

this file i can see on the ls command on the server but in the browser i dont see the file.

then i uploaded the wordpress files manually but i have the same problem that the file teneriffa-akupunktur.com/index.php gives an error.

I changed the ip 2 days ago the old ip was: 68.66.248.21 and the new ip is: 173.249.25.125

I thought maybe it is an DNS error but i can not confirm it. i deleted the cache of my browser and the DNS cache as well. 
Does anyone has an idea what is going wrong here?

thanks a lot for your kind help and sorry for bother with a small problem like that..

Update:

i found the reason php was not enabled on this domain. 
so now its working

---

