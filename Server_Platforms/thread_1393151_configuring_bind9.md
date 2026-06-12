---
title: "configuring bind9"
date: 2010-01-29
forum: Server Platforms
---

### Post by gerrybrown on 2010-01-29
Please help.

I need to setup a mail server which is with GoDaddy. It is an Ubuntu server 8.04 LTS. I want to setup Zimbra, which needs a working DNS with MX record. This is where i need help.

The domain name which i want to configure in there is 'mail.veepeegroup.com'. 

root@mail:/etc/bind/zones# dig mail.veepeegroup.com

; <<>> DiG 9.4.2-P2 <<>> mail.veepeegroup.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 64875
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 3, ADDITIONAL: 0

;; QUESTION SECTION:
;mail.veepeegroup.com.          IN      A

;; ANSWER SECTION:
mail.veepeegroup.com.   3600    IN      CNAME   pop.secureserver.net.
pop.secureserver.net.   301     IN      CNAME   pop.where.secureserver.net.
pop.where.secureserver.net. 79  IN      A       72.167.82.11

;; AUTHORITY SECTION:
where.secureserver.net. 377     IN      NS      gns2.secureserver.net.
where.secureserver.net. 377     IN      NS      gns3.secureserver.net.
where.secureserver.net. 377     IN      NS      gns1.secureserver.net.

;; Query time: 6 msec
;; SERVER: 208.109.96.1#53(208.109.96.1)
;; WHEN: Thu Jan 28 21:57:00 2010
;; MSG SIZE  rcvd: 169

In this scenario, should i install bind9 and configure it, if so, how to go about it, if not, what else should i do to make the 'mail.veepeegroup.com' to be available to send/recv mail.
I've been breaking my head and searching all over, for the past three days, without sleep. Help in this regard would be greatly appreciated. 

Thanks in advance.

---

### Post by nyu2007 on 2010-01-29
Hi,

Look like you have an DNS for lookup local. You must have an static IP for your MX Record and map to it from GoDaddy.

---

### Post by mansonthomas on 2010-01-29
I would not install bind to handle your domain MX configuration.

Go to your registar interface, setup the MX to point it to your server's IP and then setup up zimbra.
Handling a DNS server is complicated, it requires to have at least a secondary name server that I think you don't have. I handle more that 400 domain name, I know what I'm talking about, you should stick to go daddy interface to edit your mx zone.

You can also use google apps to handle your mail, it would be much more reliable (they have loads of server to handle your mail, you only have one server to handle your mail), it's far more easier than installing zimbra, which by the way, requires a dedicated server to handle the mail.

Have a look here :

[http://blog.mansonthomas.com/2008/03/how-i-setup-googleapps-premium-on.html](http://blog.mansonthomas.com/2008/03/how-i-setup-googleapps-premium-on.html)

You don't have to take the premium version, you can have up to 50 account on your domain on the standard free edition.

I've set up zimbra for one company and more than 200 google apps premium and standard edition, if you want to save time and a server, gain some reliability and feature, use google apps. (Although setting up bind and zimbra would be great to learn plenty of things)

Thomas.

---

### Post by gerrybrown on 2010-02-01
Thank you nyu2007 and mansonthomas,

First i'll try the static IP part. I want to learn Zimbra. It looks great. 

Thank you very much once again.

---

