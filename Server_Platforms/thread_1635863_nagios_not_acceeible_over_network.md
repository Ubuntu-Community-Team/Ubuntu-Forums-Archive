---
title: "nagios not acceeible over network"
date: 2010-12-02
forum: Server Platforms
---

### Post by nishikantu on 2010-12-02
Hi all,

i have configured nagios NMS on ubuntu 10.10 server ed.  the same is accessible with 
[http://localhost/nagios](http://localhost/nagios) ..but i am unable to access it over the LAN ....have turned off the system firewall and changed iptable rules to accept all ...however after doing so gave error while starting the apache server itself..

Please help Guys...!! Nube here need assistance.....

---

### Post by HugoSerrano on 2010-12-02
Hi!

Help us helping you!

Give us some more information.

$sudo /etc/init.d/apache2 start

Then paste here the error.

Regards!

---

### Post by KB1JWQ on 2010-12-02
Please disregard the previous request; if it works locally than apache running isn't your issue. :-)

Are you attempting to access the site via IP (using the name "localhost" won't work)?  If you run a netstat -antp, is apache bound to all interfaces, or just localhost?  Are you seeing error messages in your apache logs?

---

### Post by nishikantu on 2010-12-03
Thanks for the response guys,


I got the apache running somehow...but the main issue is I am accessing the nagios server over different machine itself in LAN (and not the localhost).

when issued netstat -antp command ...it seems that the apache2 is listening on 127.0.0.1 in local as well as remote addresses.

could this be the reson for the issue I am facing...but then how come when i try to access the IP of the machine only i.e. [http://192.168.226.155;](http://192.168.226.155;) it prompts me the APACHE page 
but [http://192.168.226.155/nagios](http://192.168.226.155/nagios) doesnt work.....(I am accessing this from machine with IP 192.168.226.199)...

Please help....

---

