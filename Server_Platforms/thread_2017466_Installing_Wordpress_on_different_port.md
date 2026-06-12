---
title: "Installing Wordpress on different port"
date: 2012-07-05
forum: Server Platforms
---

### Post by madu on 2012-07-05
Hi,

I have a wordpress server running already and want to have another one (on a different PC). Since both these are going to be behind the same router I need to change the port of the new wordpress server.

I have used port 8080 and have no problems when accessing the server through local LAN. But when I tried to access from outside I only get a very primitive looking page (no graphics, cant go to any link). 

I'm sure it has to be with the IP settings I put in Wordpress. I have tried different combinations and every time I change the IP in wordpress I screw up the complete installation and I have already reinstalled (found it to be easier) Ubuntu few times. So this time I need some help to get the settings right with your help.

I want to know the settings for the Wordpress and MySql.

Wordpress - Need to set two settings:
Wordpress URL
Home URL

On my first server I have set the following:
Wordpress URL: [http://www.mysite.com/wordpress](http://www.mysite.com/wordpress)
Home URL: [http://www.mysite.com](http://www.mysite.com)

And in the /etc/hosts file I have set:
127.0.0.1   [www.mysite.com](www.mysite.com)

So now that I'm running on port 8080, should I set:
Wordpress URL: [http://www.myothersite.com/wordpress](http://www.myothersite.com/wordpress)
Home URL: [http://www.myothersite.com](http://www.myothersite.com)

And in the /etc/hosts file:
127.0.0.1:8080   [www.myothersite.com](www.myothersite.com)

Also, do I need to mention 8080 when I set the host for the DB?
Usually 'localhost' is set. Should I need to mention localhost:8080 for the MySql?

Any help is greatly appreciated.
Thank you.

---

### Post by cool110 on 2012-07-05
You can't put port numbers in /etc/hosts, they need to go on the Wordpress and Home URLs
MySQL will still use port 3306

---

### Post by msammels on 2012-07-05
The only way you could install Wordpress on a different port is if you made a subdomain which used a different port. As for MySQL, the only way to have multiple ports, is multiple instances - which wouldn't be a good idea.

---

### Post by madu on 2012-07-05
Thank you very much.
I didnt know we cannot put port numbers in /etc/hosts.
I have created another domain and have URL forwarding (GoDaddy).
So there I have down [www.myothersite.com](www.myothersite.com) => <someipaddress>:8080

Thank you.

---

