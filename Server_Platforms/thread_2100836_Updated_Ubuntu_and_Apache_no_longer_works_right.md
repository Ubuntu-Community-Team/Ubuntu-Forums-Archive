---
title: "Updated Ubuntu and Apache no longer works right"
date: 2013-01-02
forum: Server Platforms
---

### Post by playoffspc on 2013-01-02
I have made some progress today, I installed Apache, toyed around with it and made some CGI scripts for simple development on my personal home network.

All was working fine and dandy. I don't quite know what happened, I rebooted after some time spent in Windows and tried to restart my web server and run into errors. At some point in this timeframe I installed some security updates for Ubuntu.

I made some mistakes, I read that I should change /etc/hosts and /etc/hostname around. Many reboots later I HOPE I am back to where I started, but apache is still being strange.

Currently I can only login using 127.0.0.1. Before that I was using my network IP address (ie: 192.168.2.4) which also let me login and develop from other computers in my network. Very handy because I can't sit on my desktop all the time, I like to use the laptop in other rooms, I even have SSH on a playbook. But I can't develop if I can't test my websites.

Before I was setting my CGIs in the code to say, submit forms to 192.168.2.4/cgi-bin/scripts and things were working fine. Now those are all broken. I don't want to go and change them to 127.0.0.1 because that doesn't solve the issue of what broke in the first place.

Most of what I am reading is about people with ~somewhat similiar issues, but they are using actual domain names. I don't want my server on the internet. It was working fine before update, on my local network, multiple computers and laptops and devices. Now I can't, I can only test locally and I don't even know if scripts will work with the 127.0.0.1 syntax but I'd prefer not to make those changes.




I get the apache2 error of "Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName".

I made no changes that I'm aware of to any of the apache conf files or logs before this error came into play so now I am wary of making changes. I don't have an httpd.conf file, only /etc/apache2/apache2.conf and ports.conf and there is no directive about ServerName in there, commented or otherwise.

---

### Post by mastablasta on 2013-01-03
> **playoffspc said:**
>  
I get the apache2 error of "Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName".
.
 
i think this is correct if you are not on internet.
 
if it says using 127.0.1.1 it could be that your Apache is already running. unless you specifically told it ***not to run*** boot then when you reboot the maschine apache is already running.
 
what happens if you go to [http://localhost](http://localhost)

---

### Post by playoffspc on 2013-01-03
> **mastablasta said:**
> i think this is correct if you are not on internet.
 
if it says using 127.0.1.1 it could be that your Apache is already running. unless you specifically told it ***not to run*** boot then when you reboot the maschine apache is already running.
 
what happens if you go to [http://localhost](http://localhost)

it works when I go to [http://localhost](http://localhost), but like I said only hours before I was not getting this message and I could login from any computer on my home network. Now I can't do that.


I added the line:

ServerName localhost



to my /etc/apache2/apache2.conf file, which removed that "Could not reliably determine the server's fully qualified domain name" warning/error. But I still get an error when I try to connect to the server via it's local IP address (ie: 192.168.2.4).

---

### Post by mastablasta on 2013-01-03
ok it could be that the port is not fowarded by ubuntu firewall? or perhaps a setting on router?
 
i too access the linux maschine from windows using it's LAN address. otherwise this would better fit in the server section. more people there that are used to dealing with server issues :-)

---

### Post by tgalati4 on 2013-01-03
Servername Myserversnamethatisthesameasinhostsfile

Make sure that your server name is spelled exactly the same as what in in your /etc/hosts file.  It should not be "localhost", otherwise, it will only respond to "localhost".

Give your server a name.  Put that same name in both the apache configuration file and in /etc/hosts with the correct, static IP address.

---

