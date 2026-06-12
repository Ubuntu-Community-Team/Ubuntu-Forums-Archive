---
title: "Ubuntu-Server on Virtual box from window."
date: 2016-11-21
forum: Virtualisation
---

### Post by siilverscr on 2016-11-21
Hi guys, fist at all, im new on the forum and also english is not my first lenguage, so pls do not be rude

I'm having a problem to connect from an outside network to my ubuntu server 16.10 with lamp stack, im using virtual box on windows 10.
In virtualbox im using bridge configuration and also i have port 80 open in mi modem with static ip address and my windows' firewall configurate.
in my apache server.conf i have:

NameVirtualHost: 190.47.165.xxx (my external ip)
NameVirtualHost: 192.168.0.26 (ip guest from ubuntu server.)

<VirtualHost 190.47.165.xxx:80 192.168.0.26:8080>
                 ServerName Server
                 ServerAlias Server
                 ServerAdmin Alexis@lamp-server  
                 DocumentRoot /var/www/html             
             
                 LogLevel info
                 ErrorLog ${APACHE_LOG_DIR}/dev.error.log
                 CustomLog ${APACHE_LOG_DIR}/dev.access.log

               <Location /server-status>
                 SetHandler server-status
               </location>
<VirtualHost>


Also when i ping from windows CMD to 192.168.0.26 (guest ip) it works.
As i said, im new on this and i try to mount a server to learn and have some fun.
Thank u guys c: i hope some answer or help!

---

### Post by mastablasta on 2016-11-22
you can ping it form local widnows, but can you connect to it from local (host OS)? is you can, then the issue is in host firewall or router firewall.

---

### Post by darkod on 2016-11-22
When you say you have port 80 open, does that mean port forwarding too? Because open port is a firewall term, but to correctly forward traffic from your router external interface to the correct private IP on your LAN, a port forwarding rule is also needed.

Another thing is that your ISP might be blocking incoming port 80, to prevent running servers at home. Did you check that the port is open with something like [www.canyouseeme.org?](www.canyouseeme.org?)

You can also use nmap directly on the ubuntu server to detect if the port is open or not. Not only by your router firewall but also by the ISP.

---

### Post by SeijiSensei on 2016-11-22
Apache is going to have problems with those references to your external IP since it can neither see nor bind to that interface.  Just define the local interface in NameVirtualHosts and set up port forwarding on your router so that traffic coming to its port 80 is forwarded back to the server's port 80.

The other, more flexible option is to use
```

NameVirtualHost *:80
<VirtualHost *:80>
ServerName      www.example.com
ServerAlias     example.com
[etc.]

```
Which matches all the interfaces on the server like localhost.

---

### Post by siilverscr on 2016-11-22
> **mastablasta said:**
> you can ping it form local widnows, but can you connect to it from local (host OS)? is you can, then the issue is in host firewall or router firewall.

i can ping the GUEST (ubuntu) address (192.168.0.26) with the windows' cmd. i cant use localhost on my browser to connect. i have the windows' firewall and my modem firewall with the ports and permissions setted to the ports for html (80) and ssh (22)

---

### Post by slickymaster on 2016-11-22
*Thread moved to **Virtualisation**.*

---

### Post by siilverscr on 2016-11-22
> **darkod said:**
> When you say you have port 80 open, does that mean port forwarding too? Because open port is a firewall term, but to correctly forward traffic from your router external interface to the correct private IP on your LAN, a port forwarding rule is also needed.

Another thing is that your ISP might be blocking incoming port 80, to prevent running servers at home. Did you check that the port is open with something like [www.canyouseeme.org?]("http://www.canyouseeme.org?")

You can also use nmap directly on the ubuntu server to detect if the port is open or not. Not only by your router firewall but also by the ISP.

if i did understand... i have the ports forwarding from my modem and also i have the rules from windows firewall:
Example of the port forwarding 
[TABLE="width: 550"]
[TR="class: dataRow"]
[TD]HTTP[/TD]
[TD]80-80[/TD]
[TD]TCP[/TD]
[TD]192.168.0.26[/TD]
[TD]8080-8080[/TD]
[/TR]
[/TABLE]
[TABLE="width: 550"]
[TR="class: dataRow"]
[TD] SSH[/TD]
[TD]22-22[/TD]
[TD]TCP[/TD]
[TD]192.168.0.26[/TD]
[TD]2221-2221[/TD]
[/TR]
[/TABLE]

//EDIT!1: im not sure if in the port forwarding ip should be internal ip of the guest  or host(ubuntu, 192.168.0.26 or windows, 192.168.0.2) remembering that i have bridge network on my virtualbox.//

and of course i have the window's firewall rules.

i think my isp is not blocking my ports because a time i did a long time ago the same thing but with XAMPP or WAMPP... and it worked well.
i used NMAP and my ubuntu server said that the PORTS are OPEN and the server is listening the ports.

0.0.0.0:3306 for mysqld listening
0.0.0.0:22 for ssh listening
:::80 apache2 listening
:::8080 apache2 listening
0.0.0.0:68 dhclient listening

and 22, 80, 3306, 8080 open with (nmap)
thank u for answerin i hope u can help me c:

> **SeijiSensei said:**
> Apache is going to have problems with those references to your external IP since it can neither see nor bind to that interface.  Just define the local interface in NameVirtualHosts and set up port forwarding on your router so that traffic coming to its port 80 is forwarded back to the server's port 80.

The other, more flexible option is to use
```

NameVirtualHost *:80
<VirtualHost *:80> 
ServerName      www.example.com
ServerAlias     example.com
[etc.]

```
Which matches all the interfaces on the server like localhost.
 
 i change everything as u said. when i try to enter from my external ip (190.47.165.xxx) it says " 190.47.165.xxx has take to long to answer"
thank u for reading and answering.

> **slickymaster said:**
> *Thread moved to **Virtualisation**.*


Thank you for moving it to the right place.

---

### Post by SeijiSensei on 2016-11-22
Are you using the stock Apache installation that comes with Ubuntu?  That is set up to use <VirtualHost *:80> by default.  

You should be creating new virtual hosts by cloning either the 000-default.conf or default-ssl.conf files in /etc/apache2/sites-available/ changing the key parameters like DocumentRoot and adding a ServerName directive for each virtual host.  When you're done, "enable" the configuration with the command "sudo a2ensite sitename" where sitename is the filename in /sites-available/ without the .conf extension.  Follow the instructions here: [https://help.ubuntu.com/lts/serverguide/httpd.html#http-configuration](https://help.ubuntu.com/lts/serverguide/httpd.html#http-configuration)

If you just accept the defaults and work within them, your server should accept requests on all interfaces.  To enable access from outside, you'll need to use the firewalling and port forwarding tools that come with your router to open its external port 80 and forward connections to it back to the Apache server.

If you intend to run only one webserver, edit 000-default.conf to fit your needs and restart apache.

You've already taken care of the most important item, having the VM used bridged networking so it can be seen from other hosts.

---

### Post by siilverscr on 2016-11-22
> **SeijiSensei said:**
> Are you using the stock Apache installation that comes with Ubuntu?  That is set up to use <VirtualHost *:80> by default.  

You should be creating new virtual hosts by cloning either the 000-default.conf or default-ssl.conf files in /etc/apache2/sites-available/ changing the key parameters like DocumentRoot and adding a ServerName directive for each virtual host.  When you're done, "enable" the configuration with the command "sudo a2ensite sitename" where sitename is the filename in /sites-available/ without the .conf extension.  Follow the instructions here: [https://help.ubuntu.com/lts/serverguide/httpd.html#http-configuration](https://help.ubuntu.com/lts/serverguide/httpd.html#http-configuration)

If you just accept the defaults and work within them, your server should accept requests on all interfaces.  To enable access from outside, you'll need to use the firewalling and port forwarding tools that come with your router to open its external port 80 and forward connections to it back to the Apache server.

If you intend to run only one webserver, edit 000-default.conf to fit your needs and restart apache.

You've already taken care of the most important item, having the VM used bridged networking so it can be seen from other hosts.

i did install lamp directly with sudo apt-get install lamp-server, also i did update later.
i did create a new virtual host by cloning the default and also i did enable de configuration with a2ensite "server-name". if i check "sites-enabled" ill find "server-name.conf"
also i have my ports and firewall configurated. now as u said ill try to run the server with 000-default.conf to see what happend. thanks for answering. ill be posting what happens.

EDIT: i did change to 000-defualt.conf and with a2dissite "serverconfiguration" and change with a2ensite "000-default", restart apache, and also i did reboot, nothing happend :'c
        i do not know what else to do

---

