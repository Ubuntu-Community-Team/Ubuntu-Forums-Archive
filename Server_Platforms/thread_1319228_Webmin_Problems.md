---
title: "Webmin Problems"
date: 2009-11-08
forum: Server Platforms
---

### Post by cf329rn on 2009-11-08
Hey Guys.

I am testing ubuntu server 8.04 in a virtual machine on my laptop. I installed webmin successfuly but whenever i try to go to the webmin page it sais in firefox and in all my other browsers it can not find the page. ive heard someone say to bridge the connections. i am pretty shure bridging is going to make the virtual machine send down internet signals through my laptops wifi. so can anybody help me. BTW im using virtualbox.:D

---

### Post by machesked on 2009-11-08
[CENTER]I would try running apt-get update on your ubuntu virtual machine to make sure the internet connection is working.  Then ifconfig to find the ip address of the virtual machine.  After that [http://ip:webminport#](http://ip:webminport#).  The webmin port number is 10000 by default.  You can also try 127.0.0.1:10000 if you bridge the connection, to point to your localhost.
[/CENTER]

---

### Post by cf329rn on 2009-11-08
it is on the internet otherwise i wouldnt beable to get webmin. the thing is i dont know how to bridge it so can you tell me

---

### Post by cf329rn on 2009-11-08
ok soi tested it and it seems its not online. it comes back with loads of errors. i need to know how to bridge it so i can get some netowork connections

---

### Post by kevin11951 on 2009-11-08
> **cf329rn said:**
> ok soi tested it and it seems its not online. it comes back with loads of errors. i need to know how to bridge it so i can get some netowork connections

In virtualbox, you would open the VMs settings, then choose "network", then choose "Attached To: Bridged Adapter", and choose the correct network interface for your network connection on the **host** machine.

---

### Post by cf329rn on 2009-11-08
> **kevin11951 said:**
> In virtualbox, you would open the VMs settings, then choose "network", then choose "Attached To: Bridged Adapter", and choose the correct network interface for your network connection on the **host** machine.

thanks dude hope it works

---

### Post by cf329rn on 2009-11-08
> **kevin11951 said:**
> In virtualbox, you would open the VMs settings, then choose "network", then choose "Attached To: Bridged Adapter", and choose the correct network interface for your network connection on the **host** machine.

didnt work. im gunna set it up on a real machine.

---

### Post by kevin11951 on 2009-11-08
> **cf329rn said:**
> didnt work. im gunna set it up on a real machine.

did you restart the guest OS (ubuntu)?

---

### Post by cf329rn on 2009-11-08
yes . i shut down the system then i used the bridge network then i starteed it and rebooted again to be safe

---

### Post by kevin11951 on 2009-11-08
> **cf329rn said:**
> yes . i shut down the system then i used the bridge network then i starteed it and rebooted again to be safe

one more thing, did you assign a static ip, or are you using DHCP?  Does your router do dhcp?

---

### Post by cf329rn on 2009-11-08
> **kevin11951 said:**
> one more thing, did you assign a static ip, or are you using DHCP?  Does your router do dhcp?

yes i did assigna static ip and yes my router supports dhcp ( its a belkin ) i havent port forwarded though should i? and on what port.10000?

---

### Post by kevin11951 on 2009-11-08
> **cf329rn said:**
> yes i did assigna static ip and yes my router supports dhcp ( its a belkin ) i havent port forwarded though should i? and on what port.10000?

post the output of ifconfig please

---

