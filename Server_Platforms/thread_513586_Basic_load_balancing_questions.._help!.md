---
title: "Basic load balancing questions.. help!"
date: 2007-07-30
forum: Server Platforms
---

### Post by brooksbp on 2007-07-30
Alright so I have some basic load balancing / scaling questions.  We're running web services at my work and we need to scale past one machine.  An ideal setup is 2x web server, 1x data server.

Right now we have one box with a static ip address.

If we get 2 web servers and 1 data server, do all those machines need their own static IP addresses? It doesn't matter that only one can connect to the internet, just as long as I can scale to the 3 total.  Do I not need static IP addresses if I run a DNS server?  Can I load balance across these 3 machines with only 1 static IP address if they're all hooked up to a switch?

How does this all work at the networking level?  I would like to use Perlbal as the software balancer and have all the machines connected via a switch... is that practical? What would you recommend for 2x web server, and a data server?

Thanks.

---

### Post by brooksbp on 2007-07-31
anyone?

---

### Post by koenn on 2007-07-31
Define what you mean by load balancing. It can mean a couple of different things.
What "load" are you expecting to balance between 2 web servers and a data server ?
And why do you need to scale to 2 or more servers ? Processing - like 1 server can't handle all the requests ? Or storage - 1 server can't hold all the data ?

---

### Post by brooksbp on 2007-07-31
Well... load balance web traffic between the two web servers... that's all the balancing... but how do you set all of this up... does each machine have to have a static ip address?

---

### Post by koenn on 2007-07-31
well, it's always a good idea to give a server a fixed ip adress (either manually or throu a dhcp reservation or whatever). It makes your live easier.

As for the load balancing, i have no experience with it but seeing that noone else is answering, I can give you a few pointers. 

There's a number of ways you can balance load between web servers. 
here's a short overview. Keep in mind that this assumes that both web servers are identical (re. the content the can serve) otherwise the whole thing doesn't make sense. 

1- "round" robin dns or other dns-based load balancing. 
Here you use DNS to spread http requests between 2 servers : for the same domain name, it will give one adres half of the time, an other adress the other half of the time. Ideally, you get 50% of the total (http request) load on each server, but with dynamic content, you may still have not-so-balanced processing load. 

2- "NAT"-based.
You let the two servers share an identical address, by means of NAT (Network adress translation), and forward requests to 1 of the 2 servers, either at random, or based on information you gather from the servers about ther processor load or network usage. 
In the latter case, you have "fail-over" : if one server is down, the other one can still offer your web service (but under heavy load)

3- Clusters
you join both servers in a cluster. To the outside world, they look like and behave as 1 machine, but between themselves, they share and balance the load. It also offers "fail over".

-----------------
4- Reverse / accelarating proxy.
You have a proxy server recaive all http requests, divide the content over 2 servers, and the proxy will get it from the appropriate server. Here, obviously, the web servers are not identical, and you move the load problem from the web server to the proxy server. Howver, the caching might help speed things up.


#1 - DNS is probably easiest (least complex) and probably sufficient

---

