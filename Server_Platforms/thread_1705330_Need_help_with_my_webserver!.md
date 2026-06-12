---
title: "Need help with my webserver!"
date: 2011-03-12
forum: Server Platforms
---

### Post by kalyptos on 2011-03-12
Hello, i will first say thanks if you take the time to read this.
Im in serious need of help. Im new to the ubuntu and linux server system.
iknow i may be on deep water here but keep in mind that im eager to learn and a fast learner.

First i will tell what ive got and what im trying to do.

I have setup my own private webserver at home, the server is running fine and works good on my local intranet. What im now is trying to do is to setup up my local server with a global domain name so i can host multiply domains on the server.

My isp has given me 1ip adress (iknow that 2is pref but ive also read that i would be fine with only one)

So with my new static ipadress from my isp im ready to rock. so i google a tutorial on google to howto setup bind9. I also registered my own nameserver with godaddy.com using the one ipadress i got from my isp.

Ok so here is where im stuck, the tutorial on the bind9 setup is using local ipadresses as example, am i suppose to use local ipadresses on the server? or should i use the statick ipadress i got from my isp? 

```
*// replace example.com with your domain name. do not forget the . after the domain name!*
*// Also, replace ns1 with the name of your DNS server*
example.com.      IN      SOA     ns1.example.com. admin.example.com. (
*// Do not modify the following lines!*
                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

[I]// Replace the following line as necessary:
// ns1 = DNS Server name
// mta = mail server name
// example.com = domain name[/I]
example.com.      IN      NS              ns1.example.com.
example.com.      IN      MX     10       mta.example.com.

*// Replace the IP address with the right IP addresses.*
www              IN      A       192.168.0.2
mta              IN      A       192.168.0.3
ns1              IN      A       192.168.0.1
```this is the /etc/bind/zones/*example.com*.db/etc/bind/zones/*example.com*.db
and as u can see the examples is reffering to local ipadresses. is this correct?
or should i replace it with my statick ipadress i got from my isp?

Im on a cable connection so i connect trough a router ([B]DSL Router X5668)

[/B]what i really need to know is how i setup up my dns and nameservers on my webserver
or if its another way i can do this.

i registred ns1 and ns2 . mydomain.com at godaddy.com using the one ipadress i have and that seemed to work fine. got a mail from godaddy that said that it was success.

so mainly what im asking is how do i configure my bind9 to work with my new nameserver.

If anyone at this forum would help me i would be Extremely happy :))

---

### Post by zadehas on 2011-03-12
You need to put your public ip (the one that your ISP assigned to you) in the zone file. This way, people trying to visit one of your domains will get your public ip.

---

### Post by wgregori on 2011-03-14
Why in the world are you setting up BIND.  This is absolutely not necessary... more importantly DNS is not easy to setup.  You have your domains registered with Godaddy... they have a great DNS system that you can just manage.... you'll have enough to learn about with setting up Apache... 

Although I run an Apache server I'm not qualified to tell you have to set it up to respond to multiple domain names.

Good luck,
Wayne

---

### Post by wongo888 on 2011-03-14
I wouldn't bother setting up your own DNS servers. There are several services (like EasyDNS in Toronto) that host DNS zone files. They handle the global redundancy issues and have a simple web interface. All that for $3 a month seems like a no brainer to me.

Take all your domain names and point them at your IP that you got from your ISP.

On your apache web server machine, create name-based virtual hosts for each domain and put your content into the different folders that make up your web roots for your domains. There is a huge doc on how to do this (read the "Basic Settings" section):

[https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)

Read it, try it and if you have any questions, come back and ask them.

---

