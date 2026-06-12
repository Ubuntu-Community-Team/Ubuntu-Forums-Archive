---
title: "Web Server Setup"
date: 2010-08-01
forum: Server Platforms
---

### Post by impresionist on 2010-08-01
Hello all,
I'm sorry for my stupid question, but I'm turning tow days, and have no idea if Mr google are not answering, or my question are not correctly given.

I'm new in server setup issues as you see...;)

So, casing of memory missing in our VPS and els, I decide to move our web-store to our own internal server...

SO under 10.4 64 bits, I installed apache/mysql/php, I configured all, and I installed and configured Magento.

When I go to localhost, it work and I get my magento web, which is located into ./var/www, the same when I call to 127.0.0.1 it word, also when I use the internal server IP, which 192.168.1.36, all it work.

So, I configured the router to drive the NAT 80/443/21 to this server devise as you see in the screen-shot, and I set up the DNS according to DynDNS all correct.

THE PROBLEM:
When I call to my public IP assigned by MyDynDNS, I get my router login screen, I mean it bring me to 192.168.1.1 ... so when I introduce the admin credentials I come into the router, I don't be drived to var/www

What wrong I'm doing, and what it's this wrong name to look for it, because I'll become really crazy...

Thanks in advance, and sorry if this issue are not related to the forum, but I don't know if I should look for it into router errors, or into Ubuntu?

Chears!

Sam

---

### Post by sampaioneto on 2010-08-01
try to run the admin section of your router on another port, what is the model of the router?

the problem is that both apache at your server and admin your router are listening on port 80, your(misconfigured)  router points to its own interface rather than driving you to apache.

---

### Post by impresionist on 2010-08-01
Thanks sampaioneto for answwer, I'm impatient just waiting for an idea how could illustrate me...
It's exactly what did you explain, the router are driving to it's own interface, instead of the server var. People in other forum, from the own router, which is comtrend, they said that I should test it from outside my network, because it's normal that I got the router interface back when I test from inside.
BUT I test it from my mobile network, and else, and it's the same...

Here you have screen shoot from my router nat config [https://dl.dropbox.com/u/2627033/Pantallazo.png](https://dl.dropbox.com/u/2627033/Pantallazo.png) 

When I appoint to my IP from inside the network I get the router interface.
From outside, 404.:(

---

### Post by Sporkman on 2010-08-02
You can try accessing your IP from outside your network by using a web proxy like [http://www.hidemyass.com](http://www.hidemyass.com) (just type your IP address in the box - it will visit your web server from the outside & display what it gets).

---

