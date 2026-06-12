---
title: "apache not available on intranet"
date: 2013-06-22
forum: Server Platforms
---

### Post by regibb on 2013-06-22
i have two machines on an intranet. we will call them bill and bob.  i have apache2 installed on bill.when i go to firefox and enter "http://bill.apache2.net/ i get
what i defined in /var/www/index.html.  if i go the the bob machine and go to firefox and enter "http://bill.apache2.net/ i get
the server not found. i have disabled the firewall and still no go...:confused: the http port 80 is open on bill.  i have got to believe that i am forgetting something
embarresingly simple...but what.

---

### Post by sanderj on 2013-06-22
bill.apache2.net? How should Bob know what the IP address of that is?

So: fill out the IP address of Bill in the URL. Probably something like 192.168.x.y or 10.x.y.z.

---

### Post by regibb on 2013-06-22
at the bob machine: [http://192.168.1.nnn/bill.apache2.net](http://192.168.1.nnn/bill.apache2.net)  resulted in 
the requested url /apache2  was not found on this server.
apache/2.2.22(ubuntu) server at 192.168.1.nnn Port 80

---

### Post by sanderj on 2013-06-22
No, just use: [http://192.168.1.nnn/](http://192.168.1.nnn/)  ... Does that work?

BTW: no need to hide your LAN IP address. Here's mine: 192.168.1.53 ... good luck with that ... ;-)

---

### Post by regibb on 2013-06-22
yes Yes YEs YES yES yeS yes...thanks

---

