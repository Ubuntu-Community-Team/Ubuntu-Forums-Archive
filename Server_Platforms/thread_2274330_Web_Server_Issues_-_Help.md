---
title: "Web Server Issues - Help"
date: 2015-04-19
forum: Server Platforms
---

### Post by Mike_Hughes on 2015-04-19
I am setting up a combination Web Server and Mail Server on one 14.04 Server. A HP Pavilion p7-1534 pc unit. Very robust compared to my last ubuntu server that was only a 32 bit install. This one sports a  1 TB Hard Drive as well. I have one site working all the way through. [www.mikealrhughes.com](www.mikealrhughes.com).  The second Domain biblematters.net ; that is going to be the mail server works locally but only if I type [http://www.biblematters.net](http://www.biblematters.net) I see the Apache welcome screen and don't see the index page I put in its folder /var/www/biblematters/public_html.  It will not work through the internet at all. Any ideas.

How do I set this server up where I don't have to physically login when it reboots. Now every time I boot it I have to log in or it sets there. Where it is going to be located will be impossible for me to have to log it back in. I plan on running it headless.

The biblematters page is actually going to be a mail server. Bible Matters is a closed mailing list. The fellow that hosted it before used mailman to host it. I saw someone mention iRedmail and had never heard about it before. If it will let me have a closed list where I moderate all mail that goes out it would work if it would be easier to set up.  

The Mikealrhughes.com site I eventually want to set up Word Press on it. I was wondering if I set it up on Word Press and someone else wants a Word Press site can the same Word Press install do more than one web page? 

So those are the things I have yet to accomplish so any help appreciated.

---

### Post by mastablasta on 2015-04-20
> **Mike_Hughes said:**
> I am setting up a combination Web Server and Mail Server on one 14.04 Server. A HP Pavilion p7-1534 pc unit. Very robust compared to my last ubuntu server that was only a 32 bit install. This one sports a  1 TB Hard Drive as well. I have one site working all the way through. [www.mikealrhughes.com]("http://www.mikealrhughes.com").  The second Domain biblematters.net ; that is going to be the mail server works locally but only if I type [http://www.biblematters.net](http://www.biblematters.net) I see the Apache welcome screen and don't see the index page I put in its folder /var/www/biblematters/public_html.  It will not work through the internet at all. Any ideas.

any errors?

did you point the domain name propperly to the website?

> 
How do I set this server up where I don't have to physically login when it reboots. Now every time I boot it I have to log in or it sets there. Where it is going to be located will be impossible for me to have to log it back in. I plan on running it headless.
use openSSH and keys: [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

did you maybe install a desktop on it? why not try some webGUI fro administering if server is headless. somethig like zentyal or Ajenti. not sure what the deal with zpenel is at the moment (the had some security issues9 or if they have a good free alternative.

dont' know much about mail servers. i am terrified of them actually... i mean to have to maintain them by myself. :)
> 
The Mikealrhughes.com site I eventually want to set up Word Press on it. I was wondering if I set it up on Word Press and someone else wants a Word Press site can the same Word Press install do more than one web page? 

definitelly yes.: [https://codex.wordpress.org/Create_A_Network](https://codex.wordpress.org/Create_A_Network)

---

### Post by Mike_Hughes on 2015-04-20
Error I receive on restarting apache2:

Restarting web server apache2
[Mon Apr 20 06:37:50.310543 2015] [core:error] [pid 25588] (EAI 2)Name or service not known: AH00547: Could not resolve host name *.com -- ignoring!
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 1xx.xxx.xxx.xxx. Set the 'ServerName' directive globally to suppress this message
   ...done.

i have Just fixed the *.com issue

Ok I fixed the *.com issue. It is resolving. Just need to fix the other issues one any help?

---

### Post by nerdtron on 2015-04-20
>  AH00558: apache2: Could not reliably determine the server's fully  qualified domain name, using 1xx.xxx.xxx.xxx. Set the 'ServerName'  directive globally to suppress this message
   ...done. 

Do you really need to fix this? I think this is a minor error and apache will still run properly.

---

### Post by Mike_Hughes on 2015-04-20
No problem with the fixing on that. I just need to get mailman up and going.

---

