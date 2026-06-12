---
title: "Creating virtual apache servers"
date: 2010-05-03
forum: Server Platforms
---

### Post by pcarlos853 on 2010-05-03
Hello, I have Webmin installed on an Ubuntu server. I currently have a successful apache server running on port 80, however I want to create a virtual host on port 81. When I try I go to servers->Apache Webserver-> Create Virtual Host I change the port to 81 and the document root to /var/port81www then I click create. How ever when I goto 192.168.1.5:81 (local ip, I know I have to port forward but its not even working local) it does not work. :confused:

Help would be much appreciated! THANKS!:D

---

### Post by noway2 on 2010-05-03
A couple of things to check for starters:
1 - did you restart or reload apache after making configuration changes to your hosts file(s)?
2 - use the command netstat -nta | grep 81 to see if anything is listening on port 81.  
3 - Once you have apache listening on 81, see if you can access it via either the local host and/or your lan.

---

### Post by pcarlos853 on 2010-05-03
I have restarted apache after changing the settings in webmin. I used the command netstat -nta l grep 81 and nothing is listening on port 81 (nothing comes up).

Thanks for your help

---

### Post by noway2 on 2010-05-05
There are two places that I know of that you will need to check:

1 - apache2.conf.  Make sure that 81 is listed as a listening port
2 - in your virtual host declaration.  You will need something like: <VirtualHost *:81>, where * can be an IP address or name.

With those declarations Apache should be listening.

Also make sure that IP tables or some other firewall isn't blocking the port.

---

### Post by Demented ZA on 2010-05-05
> **noway2 said:**
> There are two places that I know of that you will need to check:

1 - apache2.conf.  Make sure that 81 is listed as a listening port
2 - in your virtual host declaration.  You will need something like: <VirtualHost *:81>, where * can be an IP address or name.

With those declarations Apache should be listening.

Also make sure that IP tables or some other firewall isn't blocking the port.


FYI

I just opened apache2.conf and it seems it refers to another file for ports:

```
# Include ports listing
Include /etc/apache2/ports.conf
```

In my installation, however, I don't have a ports.conf file. I'm running Ubuntu 10.04.

---

### Post by noway2 on 2010-05-05
Doh your right.  I just remembered that I did a grep for the where the ports are defined this morning when I replied.  Forgot all about ports.conf.  Guess thats what I get for replying before having any coffee.

Anyway, that may be a problem.  The ports.conf is a rather simple file.  Here is mine (I am running 9.10 which I doubt is all that different in this regard.

```
NameVirtualHost *:80
NameVirtualHost *:443
Listen 80
Listen 443
#<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
#    Listen 443
#</IfModule>

```

You should have a Listen 81 directive somewhere.  
Also do a restart of Apache and look in syslog and apache log (if you have it).  it has been my experience that apache will say that it restarts ok, but it posts warnings that cause things to not work or work in a wierd fashion.

---

