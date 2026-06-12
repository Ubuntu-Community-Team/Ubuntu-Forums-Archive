---
title: "How to make my server to use a different port"
date: 2013-08-15
forum: Server Platforms
---

### Post by YBcPttm on 2013-08-15
Hi I would like my server to use port 80 instead of port 22, can some one please let me know how to do this.
I'm using Ubuntu server 12.04.2 LTS
[h=3][/h]

---

### Post by Lars Noodén on 2013-08-15
Which server?   I am going to guess that you mean your SSH server.  If that is the case look in /etc/ssh/sshd_config and look for Port or ListenAddress.  Before changing anything take at least a quick look in the manual page for [sshd_config](http://manpages.ubuntu.com/manpages/raring/en/man5/sshd_config.5.html) and look up those two directives.  Be sure to keep a backup copy of the original file, just in case.

Changing the port won't actually do much for you.  You'll get a better increase in scurity there by disabling password authentication and using keys instead.

Or did you mean another server?

---

### Post by YBcPttm on 2013-08-15
I'm trying to make a web server and I'm trying to access it over the internet and I need port 80 to do that. I will do as you suggested and then I will let you know if I was successful or not. If you have any other information for me I would really appreciate it.:)

---

### Post by Lars Noodén on 2013-08-15
For a web server, you would need nginx or Apache2.  Both of those would be managed by logging in via ssh on port 22, but the web servers themselves would be serving web pages over port 80 (http) and port 443 (https).  Which do you have nginx or Apache2?

---

### Post by YBcPttm on 2013-08-15
I have apache2

---

### Post by Lars Noodén on 2013-08-15
Apache2 will listen by default on port 80 for unencrypted connections.  Best to leave it that way and leave ssh on port 22.  A place for everything and everything in its place.

The configurations for your default virtual host will be in /etc/apache2/sites-available/000-default.conf 

If you want to set up encrypted web service (https) that will listen on port 443, but you will have to set up a certificate.

---

### Post by YBcPttm on 2013-08-15
If it's best that I leave it alone then how do I get my sites to be viewable on the internet, I had DMZ configured on my router but it didn't work.

---

### Post by Lars Noodén on 2013-08-15
To get your web sites visible on the Internet at large, you need to have your router forward ports 80 and 443 to the appropriate machine on your LAN.  The exact details vary from router to router.  What kind of router do you have?

---

### Post by cariboo on 2013-08-15
Moved to server platforms.

---

### Post by YBcPttm on 2013-08-16
The router I have is a telkom mega-105 wr

---

### Post by TheFu on 2013-08-16
> **Lars Noodén said:**
> To get your web sites visible on the Internet at large, you need to have your router forward ports 80 and 443 to the appropriate machine on your LAN.  The exact details vary from router to router.  What kind of router do you have?

Many ISPs block inbound traffic to common server ports (20, 21, 22, 25, 80, 137, 138, 139, 443, 465, 993, 8080, ... you get the idea), so there may not be any method to get this working.  You can request a port scan of your IP to see if traffic can get in or not at [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

Hopefully, you can setup your router to forward just 1 port (80) to your server and it will work.  This [http://portforward.com/english/routers/port_forwarding/Telkom/Mega-105WR/Xbox_Live_360.htm](http://portforward.com/english/routers/port_forwarding/Telkom/Mega-105WR/Xbox_Live_360.htm) shows the screens on the router. Ignore the Xbox360 specific parts.

Was ssh working from the internet on port 22 for you? If you can, you probably want to use port translation for ssh traffic to increase security. Also, if you install **fail2ban**, ssh login failures will be banned -  it is good to stop the attack attempts quicker.

BTW, does your server have a static IP address internally?

---

