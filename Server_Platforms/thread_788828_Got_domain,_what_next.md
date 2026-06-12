---
title: "Got domain, what next?"
date: 2008-05-10
forum: Server Platforms
---

### Post by Christian Christiansen on 2008-05-10
Hi, I'm new to servers and I just wanted to set up one for fun and experience mainly. I've followed [this thread]("http://ubuntuforums.org/showthread.php?t=57029") but now I'm a bit stuck. 
I've already got a domain from DynDNS, I've installed apache2, php4, mysql-server, php4-mysql and phpmyadmin on my Ubuntu 8.04 amd64 machine.
I've also  downloaded [http://sourceforge.net/project/downloading.php?groupname=xampp&filename=xampp-linux-1.4.15.tar.gz&use_mirror=puzzle]("http://sourceforge.net/project/downloading.php?groupname=xampp&filename=xampp-linux-1.4.15.tar.gz&use_mirror=puzzle") and extracted it using 
> tar xvfz xampp-linux-1.4.15.tar.gz -C /opt
My domain is [http://christianchristiansen.homelinux.com/]("http://christianchristiansen.homelinux.com/")


What next?

---

### Post by songshu on 2008-05-10
is this your server?

```
Hasbani Web Server Error Report:
Server Error: 403 Forbidden

Access denied

/doc/index.htm
```

with the ip
81.156.200.144

---

### Post by Christian Christiansen on 2008-05-10
Yes

---

### Post by songshu on 2008-05-10
well, i guess you set up apache to look at /opt/xamp as the web root.

if so then that works nicely, but you extracted it probably as a user or even root.
that means that the extracted folder is owned by that user and apache is running with different user permissions. 

it is running as user and group www-data

so what you need to do is to make sure that apache is allowed to read that folder, so you would do

chown -R www-data:www-data /opt/xamp

---

### Post by Christian Christiansen on 2008-05-10
I've got the website running and it works if I go to the link [http://localhost](http://localhost).
All I need now is to make it work if I type in [http://christianchristiansen.homelinux.com]("http://christianchristiansen.homelinux.com").

Any more help?

---

### Post by songshu on 2008-05-10
Hasbani Web Server Error Report:
Server Error: 403 Forbidden

Access denied

/doc/index.htm

this is your modem right? if it is you are close.
it would mean the request on port 80 (the web page port) needs to be guided from your modem to your server.
you need to change a setting in your modem to forward all incomming traffic on port 80 to your server.

---

### Post by Christian Christiansen on 2008-05-10
Yes that is my computer. 

How do you get it to forward all the traffic to port 80 on my computer?

---

### Post by songshu on 2008-05-10
well...

i guess it has an administartion tool that you can reach by ponting your webbrowser to your default gateway address..probably a 192.168.0.1 or something number.

hope you have the password or maybe even the manual laying around.

if you never changed the password it probably still is default, so with a bit of googling you can find the default on the web somewhere in a manual

---

### Post by Christian Christiansen on 2008-05-10
My dad said that I'm not allowed but at least I get to see it from any computer within my network. 

Thanks for your help though songshu

---

### Post by songshu on 2008-05-10
your more then welcome,

tell your dad he is a sensible guy

---

### Post by media_555 on 2008-05-21
> **Christian Christiansen said:**
> My dad said that I'm not allowed but at least I get to see it from any computer within my network. 

Thanks for your help though songshu

Daad is smart... Forwarding port 80 without enough security arrangement is really risky (for your other systems in network too..). 

Btw, I am also collecting bits and bytes on setting up home server. It is real fun.

---

