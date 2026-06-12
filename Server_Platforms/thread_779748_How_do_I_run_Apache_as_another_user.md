---
title: "How do I run Apache as another user?"
date: 2008-05-02
forum: Server Platforms
---

### Post by HyperHacker on 2008-05-02
I just installed Apache2 and created a new user/group for it, but I have no idea how to run it as that user. :confused:

---

### Post by MasterJS on 2008-05-02
it should already be running. Go to firefox and type [http://localhost](http://localhost).

---

### Post by HyperHacker on 2008-05-03
Nope, no response (i.e. cannot connect to server). Anyway I want to run it as a different user so it doesn't have access to all my stuff. (Or is that even necessary on Linux? <_<)

---

### Post by madhusudancs on 2008-05-03
First of all I would suggest you to get Apache 2 working for any user. Best way to install Apache on any Ubuntu machine >= Feisty is to use the tasksel and install the entire LAMP stack. It installs without even a single glitch.

```
$ sudo tasksel 
```

select LAMP Server and then press enter which installs Apache. I also dont understand what you mean by saying that you want to run as a different user and you dont want to access all your stuff. As it is Apache will not have access to any directory other than to your document root, i.e the directory to which localhost points. By default it is /var/www.

---

### Post by HyperHacker on 2008-05-03
Is it not a standard practice to run web services in their own limited user account to restrict how much damage they can do if compromised?

Anyway I installed the LAMP package and now it's running, but where is it? It's not using /usr/local/apache2.

---

### Post by HyperHacker on 2008-05-04
OK, so I found the root (/var/www) but I can't find httpd.conf. I searched the entire filesystem and all that came up was /usr/local/apache2/conf/httpd.conf (which it doesn't seem to be using) and /etc/apache2/httpd.conf (which is zero bytes). So I thought maybe it *was* using the former one and I'd just forgot to restart it, so I did:
```
hyperhacker@Mercury:/files/dev/win/src/mk64view$ apache2ctl restart
apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.1.66 for ServerName
httpd not running, trying to start
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
```I don't know where it got 192.168.1.66 or why it's trying to bind to 0.0.0.0:80. Unless it's because the latter file is empty, but Thunar now refuses to start >8^( so I can't check that just yet.

[edit] I rebooted, and it started up again and is still bound to localhost:80 showing the index page in /var/www. So it's not using either of those config files. :confused:

---

### Post by nowshining on 2008-05-04
all apache config files should be in

/etc/apache2/

and some are hidden sho you'll need to show hidden files.

192.168.1.66 or why it's trying to bind to 0.0.0.0:80


Do you have a router? if so 192.168.1.66 is ur router ip and 0.0.0.0:80 is your computer as well as 127.0.0.1 is all our home/computer ips, and the :80 is port 80, as port 80 is the default port for people to connect to your server ie: web/http port.

Yes to allow access to others/ie the world to  visite your webpage you will have to allow all incoming to the port you choose, or if you leave it at default allow incoming thru port 80 and inccoming thru that port thru ur router.

As for:

"hyperhacker@Mercury:/files/dev/win/src/mk64view$ apache2ctl restart
apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.1.66 for ServerName
httpd not running, trying to start
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs"

there seem to be something wrong that's blocking access to port 80, do you have any other programs running using port 80 as a server?

edit with root privs:

/etc/apache2/ports.conf

and change 

Listen 80

to 

another port higher than 1024 ex:

Listen 2500

then when u connect to ur site u'll need to add a : after the url before the / to connect to ur site


ex:

[www.example.com:2500/](www.example.com:2500/)

or

[www.example.com:2500](www.example.com:2500)


then issue in the CLI/Terminal

sudo /etc/init.d/apache2 restart

---

### Post by HyperHacker on 2008-05-04
OK, I got it, thanks. What I didn't realize was that httpd.conf is included by apache2.conf, which already has many of the basic settings, so it doesn't matter if it's empty. There's no 192.168.1.66 on my network (router is 192.168.0.1), but anyway I added my settings there and restarted it with sudo and it worked. :)

---

### Post by nowshining on 2008-05-04
glad to hear your got it all worked out.

---

