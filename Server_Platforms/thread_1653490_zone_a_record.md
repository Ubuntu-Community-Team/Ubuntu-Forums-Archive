---
title: "zone a record"
date: 2010-12-26
forum: Server Platforms
---

### Post by stargate33846 on 2010-12-26
i have a vps with a dictated ip(173.231.24.37) and a fully functional webserver. i have a free domain(as a test) from co.cc which is dalortins.co.cc( using zone A). i have the domain working. however i want to know how i could make the domain go to a different page on the server from another domain. such as , dalortins.co.cc go to /var/www/ and blahblah.egg go to /var/www/blahfolder/. i assume this in on the server end and has to do with bind9. but i have no clue about dns or bind9 and where to start. please help:)

---

### Post by robert_pectol on 2010-12-27
Assuming both domains point to the IP of your Webserver, then the DNS part is already sorted. What you are asking about is handled by the Webserver software.  If you are using Apache2, you would configure the virtual domain's document root to point to the wanted location, for each domain.

---

### Post by stargate33846 on 2010-12-28
i actualy figured this out later on after asking the question. but i couldnt get *:80 to work, i had to use the ip address

---

### Post by robert_pectol on 2010-12-28
> **stargate33846 said:**
> i actualy figured this out later on after asking the question. but i couldnt get *:80 to work, i had to use the ip address

You're welcome!  :)

---

