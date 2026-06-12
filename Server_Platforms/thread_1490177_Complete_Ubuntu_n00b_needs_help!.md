---
title: "Complete Ubuntu n00b needs help!"
date: 2010-05-21
forum: Server Platforms
---

### Post by Watchlord on 2010-05-21
I just installed Ubunut Server 10.04 an hour ago. I've been using windows before I learned to walk, but this is the 1st time I've used Linux.
 
I have the OS installed on an old Optiplex gx1. After a few minutes of head scratching I manged to get Apache2 (I don't want to install full LAMP unless absolutely neccesary) and the Gnome Desktop installed.
 
Before I go fooling around I want to ask the experts hot to do this.
 
I have an the Optiplex gx1 hooked up to a netgear router, then to a motorolla cable modem with a normal home cable service (I think port 80 is blocked).
 
Here's what I want to do: Host a lite webpage from home that I can upload a few files on (like an internet flashdrive), I want a few pictures, and some text, and then a link to a cgi proxy that is also hosted on my homeserver. All accesible from a free domain name that works with a dynamic IP address (I've looked into this, made some progress, but I'm not totally comfortable yet.)
 
Can you help me out? Anything from tutorials links to just telling me straight forward how to do it will be great.

---

### Post by Darkness Des on 2010-05-21
The only thing I can help you with is the free domain name hooked to your dynamic IP: [http://www.dyndns.com/](http://www.dyndns.com/)

Of course, it will be a subdomain but you can select it from a massive list.

---

### Post by ckennow on 2010-05-22
> **Watchlord said:**
> I just installed Ubunut Server 10.04 an hour ago. I've been using windows before I learned to walk, but this is the 1st time I've used Linux.
 
I have the OS installed on an old Optiplex gx1. After a few minutes of head scratching I manged to get Apache2 (I don't want to install full LAMP unless absolutely neccesary) and the Gnome Desktop installed.
 
Before I go fooling around I want to ask the experts hot to do this.
 
I have an the Optiplex gx1 hooked up to a netgear router, then to a motorolla cable modem with a normal home cable service (I think port 80 is blocked).
 
Here's what I want to do: Host a lite webpage from home that I can upload a few files on (like an internet flashdrive), I want a few pictures, and some text, and then a link to a cgi proxy that is also hosted on my homeserver. All accesible from a free domain name that works with a dynamic IP address (I've looked into this, made some progress, but I'm not totally comfortable yet.)
 
Can you help me out? Anything from tutorials links to just telling me straight forward how to do it will be great.

Start By installing OpenSSH then you will be able to login securely to your server with an FTP client like Filezilla. Be sure to specify port 22 when logging in. There shouldn't be an issue with installing a full LAMP server. It doesn't take up much space and it's nice to know you have MySQL and PHP installed if you ever need it.

What do you plan on hosting if I can ask?

---

### Post by HermanAB on 2010-05-22
Howdy, congrats with getting your feet wet on Linux.

Do yourself a favour and install Webmin, so that you can configure the machine using wizards.

---

