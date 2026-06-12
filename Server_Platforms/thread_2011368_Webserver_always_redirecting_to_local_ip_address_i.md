---
title: "Webserver always redirecting to local ip address instead of FQDN"
date: 2012-06-27
forum: Server Platforms
---

### Post by jmano on 2012-06-27
hello,

i am running the latest Server 12.04 on Virtualbox in Windows 7. I have a LAMP server setup and everything works fine on my internal network using the local IP to access the server from all machines in my network.

Vbox is set up to Bridged Networking and the server gets its IP adress from a DHCP Reservatin in the router. I have the HTTP service redirected to my server in the router (D-Link Dir-625) and dlinkddns setup.

From the outside of my network i can access the server's root homepage (/var/www/ where i have a phpinfo which works fine ) but when i try to go to one of my subfolders, instead of going to the address i input in the browser (for example [http://mypublicip/subfolder/](http://mypublicip/subfolder/) or [http://mydynamicdns/subfolder/](http://mydynamicdns/subfolder/) ) i get redirected to the servers local network IP ( [http://192.168.51.12/subfolder/](http://192.168.51.12/subfolder/) )

I cannot figure out if this problem is with my ubuntu server configuration or if it's a router problem, i have tried rebooting the router and checked all my /etc/hostname and /etc/hosts and the 'sites-allowed' but i can't seem to fix this.

---

### Post by LHammonds on 2012-06-27
I have a similar issue with my MediaWiki install.  I type [http://wiki.mydomain.com](http://wiki.mydomain.com) and it gets to the web server but then the address is translated into the IP address.  I got some help on these forums to try and track down what is causing it but never found the solution.

**EDIT:** I found the [discussion thread here]("http://ubuntuforums.org/showthread.php?t=1984037") which might shed some light on your particular situation.

LHammonds

---

### Post by pmla on 2012-06-29
Seems to be your apache2 configuration.
I recommend having a vhosts file per folder or directory.
You can find them in /etc/apache2/sites-available and sites-enabled.

In each vhosts file, you can try domain.com:80 or prefix.domain.com:80. Each domain should have it's own root document folder to match your directories.

---

