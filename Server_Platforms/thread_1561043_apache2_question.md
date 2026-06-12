---
title: "apache2 question"
date: 2010-08-25
forum: Server Platforms
---

### Post by felixvah on 2010-08-25
Hello everyone,

OK, I got apache2, php, mysql and phpmyadmin install successfully on ubuntu 9.10.  I test my php test and I can get to the [http://localhost](http://localhost).  

My question I only can do [http://localhost](http://localhost) on the local machine, but not any other machine within the same subnet.  If I type in the IP address then I'll get to my localhost site.  How would I access from another computer without typing the IP address?  I don't want to add the ip address into each individual host files either.  I just want to be able to type in for example: [http://mywebsite](http://mywebsite) and then it will show me what I just create on the apache2.

Thank you,

---

### Post by brettg on 2010-08-25
Ummm, the word "localhost" is your clue here.

[http://en.wikipedia.org/wiki/Localhost](http://en.wikipedia.org/wiki/Localhost)

Quite simply, you will never be able to connect to the localhost address of remote computer which is *usually* 127.0.0.1 for every computer on the network.

What you are going to need to do is assign a hostname to the "server" and then use that hostname to connect from the clients.

The clients will need to be able to resolve "hostname" to an actual IP address of course. 

The easiest way to do this if there is a small number of clients (less than 5) is to put the ip address and "hostname" into [/etc/hosts]("http://en.wikipedia.org/wiki/Hosts_%28file%29") on each of the clients.

The better (more scaleable way) is to use a dns resolver on your network. 

Large scale networks tend to use [ISC BIND]("http://www.isc.org/software/bind") for that but I prefer [dnsmasq]("http://www.thekelleys.org.uk/dnsmasq/doc.html") for small networks, especially home ones.

---

### Post by BkkBonanza on 2010-08-26
If you are using a router (usually you are), then it will run something like dnsmasq  and should have options for adding names. It then can provide name lookup for any computers on your LAN. Generally it provides DHCP to auto-assign itself as DNS resolver when a LAN computer starts up.

If that simplest option isn't doable then the next simplest is probably installing dnsmasq and adding the desired name there. Then other computers on your network need to use it as DNS resolver (or both DHCP and DNS if you want). But then whatever computer runs DNS needs to be always on. Which is why it's best handled by the router.

---

### Post by felixvah on 2010-08-26
Hey, thanks for all the information.. I'll try it out.

---

