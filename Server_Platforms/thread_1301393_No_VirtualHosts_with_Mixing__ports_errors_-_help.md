---
title: "No VirtualHosts with Mixing * ports errors - help"
date: 2009-10-26
forum: Server Platforms
---

### Post by Elliptic on 2009-10-26
Hi, I am new to Ubuntu Server, worked in a little UNIX before but a fast learner.  I have been on the forums a tons of documentation, the manuals for setting up the Web Server, etc.
 
I am doing a very simple project...  Setting up a Webserver for two domains, potentially three.  I am starting to get the "Sudo" command and the many other simple ones.  However, some instructions and how to's are not very clear.  It seems everyone talks as if you work in Ubuntu or Apache every day.  I dont so I think I am missing simple pieces.
 
Basically, I do not know where the total location or path to my files are when I type in "sudo ls"  I see my two domains where I have public_html under them where I want to put up my files via my Dreamweaver program (SFTP).  I have been able to establish connection to my server with Dreamweaver and put files up, but they got all posted to this location.  So I see all the folders and files under the "sudo ls" 
 
But I dont see my website either.  I have VirtualHost *:80 -- mixing * ports and non-*ports with a NaveVirtualHost address is not surpported, proceeding with underinded results (this message is listed 3 times then I get the last two messages:  [warn] NameVirtualHost *:80 has no VirtualHosts
 
I have edited the /etc/httpd.conf, /etc/hosts, /etc/host.conf, /etc/ports.conf, /etc/apache2/httpd.conf and others as I have been reading solutions on forums, etc... and now it is all starting to get confusing... I think I have things duplicated in areas I only need it in one place.
 
I can supply my code set up, however it is almost identical to most posted with simular issues.
 
Help...  I am running X386 Ubuntu 9.04 Server on my dedicated Dell server.  
 
Also, I am a little confused on the IP address to put in at times.. is that my www IP address or the computers IP address behind by firewall.  FYI - I do have the firewall & router set up for all the port forwarding and access correctly... rule that one out.
 
Thanx,
Eric

---

