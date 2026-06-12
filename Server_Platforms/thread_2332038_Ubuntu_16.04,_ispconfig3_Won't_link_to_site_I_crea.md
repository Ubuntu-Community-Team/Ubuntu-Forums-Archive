---
title: "Ubuntu 16.04, ispconfig3 Won't link to site I created"
date: 2016-07-27
forum: Server Platforms
---

### Post by Robert_Boutin on 2016-07-27
Hi,

I just installed Ubuntu 16.04 Server on a desktop machine in my basement and I installed a LAMP setup according to:

[https://www.howtoforge.com/tutorial/perfect-server-ubuntu-16.04-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/](https://www.howtoforge.com/tutorial/perfect-server-ubuntu-16.04-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/)

Everything SEEMED to go well.  I was able to set up a website using ispconfig3, create an email address, type 172.16.1.38/roundcube into the browser in my laptop, and log into Roundcube and send an email that actually arrived at its destination.

However...

When I type the server private ip into my browser, I get the Apache welcome page, everything is great.  But if I go into ispconfig, go to "Sites", and click on the link to the site I created, I get an "unable to Connect" error.  "Firefox can't establish a connection to the server at..."

Any ideas on why this might be happening?  I disabled ufw so that shouldn't be it.  Appreciate your help, thanks.

---

### Post by papibe on 2016-07-27
Hi Robert_Boutin.

If I understand correctly, you want to access your LAN server, from inside the LAN, thought your home's public IP?

It does work if you use the LAN IP, but not the public one?

Is that correct?

Regards.

---

### Post by Robert_Boutin on 2016-07-27
Thanks Papibe.  No, I haven't even gotten to the public ip issue yet.

My issue is that when I type the ip address into the browser, I can reach the server.  But when I go into ispconfig3 and click on the link to a site I created (which is at the identical ip address), I get the error.  So for example, I can ftp html files to the site, I just can't link to the site to view the pages.

Does that make any sense?

BTW, this is all internal to my private network, not going outside.

Thanks for your help.

---

### Post by papibe on 2016-07-27
OK, thanks.

When you got the error "Firefox can't establish a connection to the server at...", what address is being display on the browser?

Is it the same as ' 172.16.1.38/roundcube', or is it a name, or a name with a domain?

Regards.

---

### Post by Robert_Boutin on 2016-07-27
It's the name of the site I created via ispconfig3, mfelc.com

---

### Post by papibe on 2016-07-27
Thanks.

so it is:
```
mfelc.com
```
Do you have a local DNS, are you running bind, or dnsmasq?

What happens if you open a terminal and test the resolution of that?
```
nslookup mfelc.com
```
Regards.

---

### Post by Robert_Boutin on 2016-07-27
BIND is installed.

Server:   172.16.0.1
Address: 172.16.0.1#53

Non-authoritative answer:
Name:     mfelc.com
Address: 172.2.XXX.XX

172.2.XXX.XX is a static ip address I received from AT&T Uverse (which, for the record, sucks, don't ever sign up for Uverse)

---

### Post by papibe on 2016-07-28
OK. That seems to be the problem (post #2).

Usually, you can't go out from your LAN and go back trying to get to your own public IP. Even if the port is being correctly forwarded.

The feature to allow this behavior is called NAT loopback, and it is not available in consumer routers. It may though be available on more pricey routers, or in open source firmware like OpenWRT.

The way to test access to your server from the 'outside' is using either your phone (while not connected to WiFi), or through a VPS, or actually from the outside, like a public library, or a friend's house. 

Alternatively, you could set up bind to resolve requests to 'mfelc.com' (from the LAN) to 172.16.1.38.

Does that help? Let us know if you have more questions, and how it goes.

Regards.

---

### Post by Robert_Boutin on 2016-07-28
Ah, ok.  I thought when I clicked the link in ispconfig3 that it was connecting to my server's private ip address that I assigned when I created the website when in fact it is going out and looking up the existing A-Record, seeing the public ip address, and trying to connect that way.  And even though I haven't opened up the server yet to the internet, my router likely won't permit that traffic anyway.

That makes sense, thanks a lot for the explanation.

---

### Post by papibe on 2016-07-28
> **Robert_Boutin said:**
> And even though I haven't opened up the server yet to the internet, my router likely won't permit that traffic anyway.
Just to be precise...

It won't allow the loopback. However, if you set up the proper port forwarding rules, it would allow requests and responses from the outside.

As a side note, the latter is a technical assessment, in other words, it should work, and it works for a lot of people. Nonetheless, setting a web server at home may be in violations on your ISP agreement. Sometimes if the traffic is slow, they don't enforce it. Other times, they just block the standard http port (80), and technically you could have a server on another port.

Just some thoughts. Let us know how it goes.
Regards.

---

