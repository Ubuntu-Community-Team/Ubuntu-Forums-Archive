---
title: "Cant access apache or any server over my primary ip address"
date: 2010-05-17
forum: Server Platforms
---

### Post by creamers on 2010-05-17
Ok I have no idea what is going on here and this is the second time it has done this but. I just installed Lucid Lynx Desktop Edition for my Server. I have installed apache php5 mysql binarys. I have 3 ips on the machine 10.0.1.30, 10.0.1.37, 10.0.1.38. .30 is the main ip 10/100 the rest are 10,100,1000 ports. I can only access Apache 2.2 over .37 or .38 but not .30


I have not used Ubuntu alot but I am starting to and this really pisses me off since all my computer have aliases to the machine through .30

Any one have an Idea what is going on here.

---

### Post by creamers on 2010-05-17
OK not what the heck it just switched were .30 and .38 can be access is this some type of first connection thing because I need one ip that I can trust for my web server so it doesnt change every reboot.


Sorry for double posting I didnt see the edit button apperently I got logged out.

---

### Post by elias832 on 2010-05-19
So if i understand this correctly, you want to access the apache server on any of .30 .37 and .38, and it will all point to the same /var/www/xxxx folder? or each ip is supposed to point to a different folder?

---

### Post by creamers on 2010-05-19
No not virtual hosts I just want each ip to point to the server. It is the same deal with programs like ssh and ftp where one or two ports decide to block incoming connections.

---

### Post by elias832 on 2010-05-19
I think that has to be done through iptables....

---

### Post by creamers on 2010-05-19
Thing is I have never set iptables and it happened when I install it and alternated every single time.

---

