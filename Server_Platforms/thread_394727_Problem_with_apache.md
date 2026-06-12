---
title: "Problem with apache"
date: 2007-03-27
forum: Server Platforms
---

### Post by darkos on 2007-03-27
Hello folks,
I've got kubuntu 6.10 edgy installed on my pc.
Im installing apache2 with sudo apt-get install apache2. The files located in /var/www are accessible through a browser for the same pc and over the local network too, but not for users over the internet. Is there some bind-option for apache that i should disable?
any help appreciated :)

---

### Post by kidders on 2007-03-27
Hi there,

Could you describe your network configuration? For instance, how many network interfaces have you got, and what are they connected to?

Is inbound traffic being routed to your Apache server correctly?

---

### Post by didijeeeke on 2007-03-27
are you using a router NAT? 
you need port forwarding  in that case
it is also possible your provider blocked port 80 
try using a different port 8080 for example

---

### Post by darkos on 2007-03-27
First of all i don't think the port 80 is being blocked by my isp, because then i wouldn't be able to browse Internet sites at all. I have 2 pc's connected on an adsl-modem-router usr 9108 with a dhcp server. i didn't understand this about the inbound traffic, could you be a little more specific on that one?if the other pc on the network connects to [http://192.168.1.3](http://192.168.1.3) (the servers internal address) it shows normally the apache site, so the routing is ok. I'll try using another port.

---

### Post by darkos on 2007-03-27
Seems to be working with other ports...i think the router is using port 80 for something, because when i tried forwarding it, it said something about adsl gateway web server and that it would be moved to 8080, but after that it still didn't work. Anyways ill be using apache with a different port now. Thanks for your help :)

---

### Post by kidders on 2007-03-27
> **darkos said:**
> First of all i don't think the port 80 is being blocked by my isp, because then i wouldn't be able to browse Internet sites at all.
From your perspective, network traffic flows in two directions (in and out). It's possible (indeed it's *likely*, in certain countries) that your ISP is blocking inbound traffic on port 80, which would not affect your ability to browse the web. Mention the name of your ISP in your next post ... depending on where you live, someone may be able to tell you for sure.

---

### Post by darkos on 2007-03-28
Indeed! I think you are right. I heard that other isps here block inbound traffic on port 80. I'm living n Greece and my isp is Forthnet.

---

### Post by pppetter on 2007-03-28
If you have configured your modem/router thingy so that you can remotely change the settings in it, then that's your problem, it's worth checking out :)

---

