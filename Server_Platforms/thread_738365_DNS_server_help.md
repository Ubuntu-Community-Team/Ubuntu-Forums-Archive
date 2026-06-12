---
title: "DNS server help"
date: 2008-03-28
forum: Server Platforms
---

### Post by theugleymonkey on 2008-03-28
I am trying to start to understand DNS servers fully so i want to create my own.  what i want to know is if i create my own DNS server can it act like a public server.  what i am really trying to say is. what will it be able to do for me after i make one.

---

### Post by Dr Small on 2008-03-28
If you are on a network, the DNS server coulde be handy for setting up private domains for different network computers.

It is also interesting to use domains for Apache VirtualHosts :)

Dr Small

---

### Post by kool_kat_os on 2008-03-28
A good dns server is BIND9

```
sudo apt-get install bind9
```

---

### Post by kool_kat_os on 2008-03-28
To understand them i found this link
[http://computer.howstuffworks.com/dns.htm](http://computer.howstuffworks.com/dns.htm)

---

### Post by kool_kat_os on 2008-03-28
But if you just want to set up a webserver just install apache

```
sudo apt-get install apache2
```

---

### Post by theugleymonkey on 2008-03-29
interesting ok thanks

---

### Post by Mr. C. on 2008-03-30
Here are some lesson/lecture/lab/homework that will perhaps be useful in your learning DNS.  Try the DNS lab in DNS1:

[http://cis68c2.mikecappella.com/](http://cis68c2.mikecappella.com/)

Skip the steps about installing software, or tailor to Ubuntu as necessary.  Focus on Bind configuration and testing.

---

### Post by dantheman3212 on 2008-03-30
Doing your own DNS server is relatively easy, especially in Ubuntu. Bind9 is one of the most stable environments I've used.

You first need to get yourself a domain name registrar, I used AITdomains.com, and you point it to your own name server, which you set up. Heres a great guide one what to do.


[http://news.softpedia.com/news/How-to-Host-Your-Own-Domain-With-Bind9-on-Ubuntu-49585.shtml]("http://news.softpedia.com/news/How-to-Host-Your-Own-Domain-With-Bind9-on-Ubuntu-49585.shtml")

---

### Post by TheS0urce on 2008-04-25
[http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/)

Fast and easy way to get your DNS server running.  Make sure always have the lastest BIND for security reasons.

---

