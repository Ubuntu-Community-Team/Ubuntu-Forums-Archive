---
title: "Ubuntu server apache killed?"
date: 2008-10-23
forum: Server Platforms
---

### Post by LOG123 on 2008-10-23
one day i went to log in to my site and when i tried to go there (BTW this is from WITHIN the server itself) it says Firefox can't establish a connection to the server at [www.mysite.com](www.mysite.com) (not the real name) and i was confused :confused: i mean SERIOUSLY it was from THE SERVERS WEB BROWSER!!! apache webserver 2 is installed and running! any help would be GREATLY appreciated!


LOG123

---

### Post by tunggul on 2008-10-23
First, you should check whether apache daemon (httpd) is still running. Use ps ax for that. If the daemon for some reason is not active, try restart it (w/ /etc/init.d/apache restart or /etc/init.d/apache2 restart if you're using apache2). Then check the status w/ ps ax again.
If the daemon fail to start, check /var/log/syslog and /var/log/apache/error.log (or /var/log/apache2/error.log for apache2) to see the cause

---

### Post by LOG123 on 2008-10-23
> **tunggul said:**
> First, you should check whether apache daemon (httpd) is still running. Use ps ax for that. If the daemon for some reason is not active, try restart it (w/ /etc/init.d/apache restart or /etc/init.d/apache2 restart if you're using apache2). Then check the status w/ ps ax again.
If the daemon fail to start, check /var/log/syslog and /var/log/apache/error.log (or /var/log/apache2/error.log for apache2) to see the cause

:-O i am so stupid :lolflag::redface:

---

### Post by LOG123 on 2008-10-26
I'm gonna have to revive this thread because... well i think apache's dead again here's the error I'm getting:
[] [error] VirtualHost -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
Now I'm REALLY stumped:(:confused:

LOG123

---

### Post by LOG123 on 2008-11-01
come on! its still happening!!:(

---

### Post by LOG123 on 2008-11-02
Bump.

---

### Post by LOG123 on 2008-11-02
i messed around with Apache and now this is the error I'm getting:
[error] VirtualHost myip:0 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[] [error] VirtualHost myip:0 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[] [error] VirtualHost myip:0 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[] [error] VirtualHost myip:0 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
                                                                         [ OK ]
can someone tell me what i'm doing wrong even if its a stupid mistake?:confused:

---

### Post by FlaHAM on 2008-11-02
There are two statements in ports.conf.
One is for VIM and the other for for the base Server.
Comment out the one for the Virtual Server so that only the 
listen statement is enabled.

I added a second statement to the file for port 800 and restarted
apache. Port 80 works, but not 800. :(

---

### Post by LOG123 on 2008-11-02
> **FlaHAM said:**
> There are two statements in ports.conf.
One is for VIM and the other for for the base Server.
Comment out the one for the Virtual Server so that only the 
listen statement is enabled.

I added a second statement to the file for port 800 and restarted
apache. Port 80 works, but not 800. :(

i checked the configuration and this is all that is there:
Listen 80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>

---

