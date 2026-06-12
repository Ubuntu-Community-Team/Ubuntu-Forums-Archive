---
title: "PowerDNS Compilation or Older Version"
date: 2009-08-27
forum: Server Platforms
---

### Post by emonhaider on 2009-08-27
Hello!
 
I am fairly new to Ubuntu/Linux.
 
I have 8.10 setup with PowerDNS latest version. I intend to use it as a secondary DNS Server. The primary server is Microsoft DNS. There is an issue with the latest PowerDNS (it is too strict in parsing messages during AXFR), and zone transfer fails with a 'Failed to parse domain 'xxx' ....'
 
With some searches I found two work arounds: going back to version 2.9.20 (I think) or make some changes in a specific file and compile your own copy of PowerDNS.
 
I was unable to obtain an older version package of powerDNS, and I don't know how to compile it either.
 
I will appreciate any help from this great community.
 
 
Thanks.
Haider

---

### Post by cariboo on 2009-08-28
Have a look at dnsmasq, it is in the repositories, It may solve your problem.

---

### Post by sh1ny on 2009-08-28
> **emonhaider said:**
> Hello!
 
I am fairly new to Ubuntu/Linux.
 
I have 8.10 setup with PowerDNS latest version. I intend to use it as a secondary DNS Server. The primary server is Microsoft DNS. There is an issue with the latest PowerDNS (it is too strict in parsing messages during AXFR), and zone transfer fails with a 'Failed to parse domain 'xxx' ....'
 
With some searches I found two work arounds: going back to version 2.9.20 (I think) or make some changes in a specific file and compile your own copy of PowerDNS.
 
I was unable to obtain an older version package of powerDNS, and I don't know how to compile it either.
 
I will appreciate any help from this great community.
 
 
Thanks.
Haider

I'm in the exact same scenario , using jaunty with 2.9.21 powerDNS which is slave to a microsoft DNS. It is working fine. You need to make sure that the msDNS doesn't have the BIND compatibility checkbox checked or axfr will fail. If you need, i'll dig details from our Windows guys.

P.S. Before jaunty we were running intrepid and powerDNS < - > msDNS was working fine.

---

### Post by emonhaider on 2009-08-29
Thanks to both of you! I will look into Bind compatibility option in MS DNS and see if that helps.
 
Does dnsmasq use MySQL as well?

---

### Post by emonhaider on 2009-08-29
Thank you! It is working now.
 
The option is 'Bind Secondaries' under 'Advanced' Tab of DNS Server Properties.
 
It was the supermaster feature of PowerDNS that sold me.

---

