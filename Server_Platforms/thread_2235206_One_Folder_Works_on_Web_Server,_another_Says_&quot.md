---
title: "One Folder Works on Web Server, another Says &quot;Not Found&quot; when I browse to it"
date: 2014-07-19
forum: Server Platforms
---

### Post by bmcgonag on 2014-07-19
I am running Ubuntu 14.04 as a web server with LAMP installed. 

I have an owncloud instance running in the /var/www directory, and can browse to it and hit it fine from any computer on my network.  I can also use the Sync clinet with no issue. 

I have just unzipped a folder to the /var/www directory for Wallabag (which I am successfully running on a Digital Ocean droplet with no issue), and when I browse to the address 192.168.1.9/wallabag I get an error 

[COLOR=#000000][FONT=Times New Roman]"The requested URL /wallabag was not found on this server"

I've double and triple checked that i'm spelling the folder name exaclty the same.

I see the basic index.html file in the /var/www root, and I also cannot get it to load. 

Any help is greatly appreciated.[/FONT][/COLOR]

---

### Post by Doug S on 2014-07-19
The default documentroot is now /var/www/html whereas it used to be /var/www.

---

### Post by bmcgonag on 2014-07-20
Yep! That was it Doug S., when did that change?  Thanks so much.

---

### Post by Doug S on 2014-07-20
> **bmcgonag said:**
> Yep! That was it Doug S., when did that change?  Thanks so much.It changed sometime late in the 14.04 development cycle. It was after some of us had tested, a few times, that area of the Ubuntu Serverguide and Ubuntu manual tests. The Ubuntu serverguide will be updated in a pending point release, in a week or two. [see also]("https://bugs.launchpad.net/serverguide/+bug/1305313").

---

