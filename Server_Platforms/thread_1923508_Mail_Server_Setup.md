---
title: "Mail Server Setup"
date: 2012-02-10
forum: Server Platforms
---

### Post by XswordfishX on 2012-02-10
i just installed ubuntu server 11.10 because i want to establish mail  server, our company have an existing mail system using the godaddy from which our  website is currently being hosted, the problem is that each user account  is limited to 20mb only and quite slow. 

As of now, my current scenario is that, i have 5 available  static IP address from our internet provider, can i use these ip address  as host address of the mail server using the ubuntu? if so? what would  be the steps? 
thanks in advance..

---

### Post by collisionystm on 2012-02-10
> **XswordfishX said:**
> i just installed ubuntu server 11.10 because i want to establish mail  server, our company have an existing mail system using the godaddy from which our  website is currently being hosted, the problem is that each user account  is limited to 20mb only and quite slow. 

As of now, my current scenario is that, i have 5 available  static IP address from our internet provider, can i use these ip address  as host address of the mail server using the ubuntu? if so? what would  be the steps? 
thanks in advance..


First

I really recommend you use Google mail for your work. Google Apps business is great. We use it in a 100 employee environment. Each user gets 25gb of space.

2nd

I really recommend you use zentyal as a mail server if you choose to host your own.

3rd

You would 

A) Put the mail server directly on the internet ( generally not recommended ).
B) Place a router on the internet and forward smtp traffic to your mail server.

Either way you would need to get your server up, test its emailing and finally change your MX record from go daddy to your static address that points to the new mail server.

---

### Post by collisionystm on 2012-02-10
> **XswordfishX said:**
> i just installed ubuntu server 11.10 because i want to establish mail  server, our company have an existing mail system using the godaddy from which our  website is currently being hosted, the problem is that each user account  is limited to 20mb only and quite slow. 

As of now, my current scenario is that, i have 5 available  static IP address from our internet provider, can i use these ip address  as host address of the mail server using the ubuntu? if so? what would  be the steps? 
thanks in advance..


First

I really recommend you use Google mail for your work. Google Apps business is great. We use it in a 100 employee environment. Each user gets 25gb of space.

2nd

I really recommend you use zentyal as a mail server if you choose to host your own. It is based on 10.04 LTS and has a very very good web interface.

3rd

You would 

A) Put the mail server directly on the internet ( generally not recommended ).
B) Place a router on the internet and forward smtp traffic to your mail server.

Either way you would need to get your server up, test its emailing and finally change your MX record from go daddy to your static address that points to the new mail server.

---

### Post by XswordfishX on 2012-02-11
> **collisionystm said:**
> First

I really recommend you use Google mail for your work. Google Apps business is great. We use it in a 100 employee environment. Each user gets 25gb of space.

2nd

I really recommend you use zentyal as a mail server if you choose to host your own.

3rd

You would 

A) Put the mail server directly on the internet ( generally not recommended ).
B) Place a router on the internet and forward smtp traffic to your mail server.

Either way you would need to get your server up, test its emailing and finally change your MX record from go daddy to your static address that points to the new mail server.


Thank you for the quick reply and really appreciate it, i will try zentyal, anyway im still on the process of gathering more information about opensource solutions about mail servers.

---

### Post by tamkt on 2012-02-11
You can try Zimbra Server
[http://www.zimbra.com/downloads/os-downloads.html](http://www.zimbra.com/downloads/os-downloads.html)

---

### Post by HermanAB on 2012-02-12
The easiest mail server is Citadel.  The Easy Install script runs in about 20 minutes and then it just works.  Citadel can handle enormous amounts of mail - up to 256 Terabyte of mail in a BerkeleyDB.

---

