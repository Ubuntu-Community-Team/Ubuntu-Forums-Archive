---
title: "I just got my very first server up an running -- Now What?"
date: 2012-06-11
forum: Server Platforms
---

### Post by HunterDX77M on 2012-06-11
Hi all,

Out of curiosity, I decided to take an old computer of mine and install Ubuntu Server 12.10. Now that this server is up an running (i.e., I can connect to it and move files and such), I was wondering what can I do with it? I want to try something fun, but doable.

[COLOR="Red"]**[COLOR="DarkRed"]I am a complete noob when it comes to servers and networking[/COLOR]**[/COLOR], so if you have any suggestions please explain them to me as if I were your grandmother who still thinks tweets are what the birds in her backyard do. 

The the computer I made it out of is really old and has pretty disappointing specs: 256MB of RAM, 1.8 GHz Pentium 4. I can triple the memory though with a $10 purchase from Amazon, if I feel a project is worth undertaking. Thanks and I hope to hear some great responses.

---

### Post by MG&amp;TL on 2012-06-11
You could run a local webserver for web development, or use NFS/Samba for file sharing/backup. These are just what I use my server for, so just some suggestions. There's ubuntu wiki pages that explain how to make them much better than I could.

---

### Post by CharlesA on 2012-06-11
> **MG&TL said:**
> You could run a local webserver for web development, or use NFS/Samba for file sharing/backup. These are just what I use my server for, so just some suggestions. There's ubuntu wiki pages that explain how to make them much better than I could.
Same here.

It's a good place to start.

---

### Post by HunterDX77M on 2012-06-11
Okay, I want to give the web server thing a try. I don't have many web development skills, but I'd still like to give it a go and see where it takes me. Where can I find resources to get started on that? :)

---

### Post by CharlesA on 2012-06-11
[http://www.w3schools.com/](http://www.w3schools.com/)

---

### Post by HunterDX77M on 2012-06-11
> **CharlesA said:**
> [http://www.w3schools.com/](http://www.w3schools.com/)

Sorry, I meant resources for setting up a server. I already know some HTML, JS and PHP (and I learned them from W3 Schools :)).

---

### Post by CharlesA on 2012-06-11
Check here:
[http://woodel.com/](http://woodel.com/)

[https://help.ubuntu.com/12.04/serverguide/index.html](https://help.ubuntu.com/12.04/serverguide/index.html)

---

### Post by MG&amp;TL on 2012-06-11
Also: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by anonymouschief on 2012-06-11
Here are some more ideas:
**[7 Cool Things to Do With Linux]("http://www.davehayes.org/2009/01/16/7-cool-things-to-do-with-linux")**

I use my server as an enterprise class VoIP phone system. It is so much fun managing the OS, as much as managing apps that the machine serves.

Here are my favourite maintenance tasks:
[LIST]
[*]Watching the server logs and then fixing the problems reported.
[*]Managing backups.
[/LIST]

My favourite folder in the system is /var/log :)

---

### Post by LHammonds on 2012-06-12
So far, I have used Ubuntu for servers providing MediaWiki, MySQL, Nagios network monitoring and Zimbra mail server.  See links in sig for details.

**EDIT:** @anonymouschief, nice link!  I was thinking about some kind of LAN-based media server to allow access to stored video to various TVs around the company.

LHammonds

---

### Post by lisati on 2012-06-12
A couple of thoughts.

My setting up a server was partly out of curiosity, and partly as a replacement for Yahoo Geocities when their free web pages were shut down. In time I added email capabilities, again partly out of curiosity, but mainly due to being dissatisfied with the way the email providers I was using handle spam. File sharing hasn't been a priority, I haven't had the need.

---

### Post by nj_peeps on 2012-06-12
You could also run a jabber server, and it does not require a ton of resources, and is very easy to setup (ejabberd). You could also set it up as a NAS, and share files via NFS or Samba.  
Or if you are into using VoIP at all, you could run Asterisk :)

---

### Post by freakinjonathan on 2012-06-12
Google how to install a lamp stack

Linux/Apache/Mysql/php

These is standard software as far as web servers go.

---

### Post by freakinjonathan on 2012-06-12
> **HunterDX77M said:**
> Sorry, I meant resources for setting up a server. I already know some HTML, JS and PHP (and I learned them from W3 Schools :)).
Google how to install a lamp stack

Linux apache mysql and php 

pretty much standard as far as web server software goes.

---

