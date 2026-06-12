---
title: "external DNS issues"
date: 2012-04-05
forum: Server Platforms
---

### Post by Yizi on 2012-04-05
I'm trying to setup two sites on my server (ubuntu 10.04). I have managed to configure the Apache to do what it suppose to but I'm having problem point my domain to my ip address. I'm using the namecheap.com DNS service which is free and that's where the domain is registered. 

at the moment I have pointed the ns1.domain and ns2.domain to my IP address (I only have 1 static IP address) and then change the DNS names on the domain to the DNS names I setup but nothing is working now, I tried pinging the domain too but host was unknown.

Anyone has any experience regarding this?

Thanks!

---

### Post by darkod on 2012-04-05
Hold on, what exactly did you do?

Your server is on your home network and has a static private IP, right? Did you try to open it from a computer on your home network directly with entering the private IP? Does it work?

Once you get that working, you need to tell your router to forward port 80 (and maybe 443 if you plan to use SSL) to your server private IP.

What do you plan to use namecheap for, is your domain registered there? In that case you simply have to create the A records with the static IP of your router, so that the DNS servers send the traffic to your router which will forward it to your server.

---

