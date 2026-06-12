---
title: "dyn.com and godaddy"
date: 2012-11-11
forum: The Cafe
---

### Post by prodrumernate on 2012-11-11
is godaddy.com premium DNS the same as dyn.com standard DNS? i want to know because id rather go through go daddy and pay a couple bucks than pay 30 and go through dyn.com.ive used godaddy for years.i live just a few miles from the godaddy center in scottsdale, az.so its more convenient for me...

but want to know if they are the same.im setting up my home server with a domain name ill purchase soon.but im not sure also if i have a fixed external ip address or not or if there is a way to set up my server for world access.so maybe purchasing some kinda DNS type manager that will allow me to use my own domain name and my own server.id rather do.and not sure if godaddy's premium DNS is the same as dyn.com standard DNS.

---

### Post by oldos2er on 2012-11-11
Not an Ubuntu support question; moved to Community Cafe.

---

### Post by prodrumernate on 2012-11-11
> **oldos2er said:**
> Not an Ubuntu support question; moved to Community Cafe.

it pertains to using it on my ubuntu home server. to which ill need to ask more questions on how to set it up on ubuntu....

---

### Post by gordintoronto on 2012-11-11
If you don't know, then you don't have a fixed IP address. In other words, every time you reboot your modem, you will have a different IP address. This web site:
[http://whatismyipaddress.com/](http://whatismyipaddress.com/)
might help your understanding.

Many ISPs do not allow "residential" clients to run a web server. Check the Terms of Service for your ISP. My only relationship with Go Daddy is as a customer. If you sign up for multi-year web hosting, it's pretty cheap, especially with "30% off" renewal.

---

### Post by sandyd on 2012-11-12
> **prodrumernate said:**
> is godaddy.com premium DNS the same as dyn.com standard DNS? i want to know because id rather go through go daddy and pay a couple bucks than pay 30 and go through dyn.com.ive used godaddy for years.i live just a few miles from the godaddy center in scottsdale, az.so its more convenient for me...

but want to know if they are the same.im setting up my home server with a domain name ill purchase soon.but im not sure also if i have a fixed external ip address or not or if there is a way to set up my server for world access.so maybe purchasing some kinda DNS type manager that will allow me to use my own domain name and my own server.id rather do.and not sure if godaddy's premium DNS is the same as dyn.com standard DNS.

a) Is godaddy.com the same as dyn.com standard dns
nope. Dyn.com is more business/enterprise oriented, or websites that can't afford to have DNS outages. They have  SLA if I remember correctly, There are others such as dnsmadeeasy, zoneedit, .etc .etc

b) Use dns.he.net - they have dynamic DNS support

also, +1 to the previous poster's reccomendation to check their ISP's TOS. Some actually block port 80, unless you have a business-class connection with them

---

