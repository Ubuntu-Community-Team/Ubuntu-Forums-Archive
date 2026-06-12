---
title: "DNS problems &quot;SERVFAIL&quot;"
date: 2008-05-17
forum: Server Platforms
---

### Post by razta on 2008-05-17
Hello,
Wanted to set up a webserver today for my wlan, 1 x ubuntu, 1 x winxp and wireless router. Using ubuntu hardy heron as the webserver, installed apache2, php5 and bind9. 

Bind9 seems to work fine:
```
$ sudo /etc/init.d/bind9 restart 
 * Stopping domain name service... bind                                  [ OK ] 
 * Starting domain name service... bind                                  [ OK ]
```

However when I go to [www.curzonplace.com](www.curzonplace.com) which is the DNS name I set up for the webserver, I get a "page not found" error, on the xp machine it goes to the actual [www.curzonplace.com](www.curzonplace.com) website and not the one I set up internaly.

Dig output:
```
$ dig curzonplace.com

; <<>> DiG 9.4.2 <<>> curzonplace.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 63714
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;curzonplace.com.		IN	A

;; Query time: 1 msec
;; SERVER: 192.168.0.3#53(192.168.0.3)
;; WHEN: Sun May 18 00:46:43 2008
;; MSG SIZE  rcvd: 33

```

Ping output:
```
$ ping www.curzonplace.com
ping: unknown host www.curzonplace.com

```

Any one know how I can fix this? Think im in way over my head here, first time ive tried setting up a webserver. Thanks in advance for any help.

---

### Post by Thirtysixway on 2008-05-17
Did you set your dns server address on your router and/or xp system to point to your Ubuntu machine?  This would be the first thing to check.

---

### Post by razta on 2008-05-17
I hadnt changed them, changed them both now. How stupid could I be? lol

The ubuntu and xp are now showing "address not found" for [www.curzonplace.com](www.curzonplace.com).

Can connect to other domains fine, ei google

Thank you for your reply.

---

### Post by Thirtysixway on 2008-05-17
Hmm.  I would double check your apache configuration to be setup to accept connections for [www.curzonplace.com](www.curzonplace.com).

---

### Post by razta on 2008-05-17
To be honest I havent messed around with the Apache conf files, I assumed they would automatically point to /www/. I will have a look at them now, thanks again for your help.

EDIT---

Cant seem to figure out what to edit within apache to get it working, looked at a few docs and readmes but nothing so far.

EDIT---

Created a directory called "/var/www/curzonplace.com" and put index.html in the directory but still nothing.

EDIT---

Got this error when starting apache:
> $ sudo /usr/sbin/apache2ctl start
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (pid 14122) already running


EDIT---

Ok... got rid of that error...

I amended the following to the end of apache2.conf:
> # ServerName
ServerName curzonplace.com

Restarted apache.

Gets rid of the error, but still no joy, if I go to [http://127.0.0.1](http://127.0.0.1), that works.

---

### Post by razta on 2008-05-17
FIXED!!!!

Amended the following to /etc/hosts:
> 192.168.0.3     curzonplace.com

Now works fine!

---

### Post by juan@forum on 2008-05-18
it is not the best solution, your DNS service is not working...

---

