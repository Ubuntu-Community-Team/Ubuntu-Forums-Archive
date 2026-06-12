---
title: "FQDN Domain Name / Server IP Assignment"
date: 2009-07-27
forum: Server Platforms
---

### Post by Nuebytes738 on 2009-07-27
Hi, I'm new to the community, but I got bit by the Ubuntu bug and I'm caught up now; i love.
 
I am working on network technologies, and getting into motion of setting up a server with Ubuntu 9.
 
I would like to setup a mail server for my own use, family down the road then friends. When referencing fully qualified domain name, to setup a mail server domain name, is that a reference to needing to setup / register a domain name, then having the the service, such as godaddy.com host the domain to resolve my new domain name to my static ip address of my internet connection?
 
Or for examply, my new domain will be resolved from my current ISP; my ISP's dns servers would resolve my domain name to my static assigned IP address?
 
At the moment, I got message traffic at the very basic level where on my test box, via the command line, one user account can send a basic email message to another account; I have Postfix install.
 
thank you for your time in advance... regards Nuebytes738

---

### Post by windependence on 2009-07-28
Setting up a full blown mail server is not exactly an easy project for a beginner.

You will point your domain from GoDaddy's DNS control panel to your static IP address (and you will need one to do it correctly). DNS is rarely done at the ISP level. You will need to set up MX records in your DNS control panel and you should set up reverse DNS or many mail servers will not talk to yours. Reverse DNS will most likely need to be set up with the place you got your static IP from (probably your ISP). 

This is just scratching the surface. There are mony other tings you will ned to set up to get everything working properly. If you are new at Linux, it can be daunting.

-Tim

---

### Post by Nuebytes738 on 2009-07-29
[Windependence,]("http://ubuntuforums.org/member.php?u=291170")

thank you for your reply, you got me in a good direction, wasn't too sure. I've got some network technology understanding, not a veteran or such.  Ubuntu is great, I'm currently working from the command prompt on my ubuntu development box; I've been interested in completing some projects and learning messaging / communication for awhile, ubuntu doesn't give me all that licensing issues like. . hmm.. heh, M.S.

thank for your reply! v/r Neubytes738

---

