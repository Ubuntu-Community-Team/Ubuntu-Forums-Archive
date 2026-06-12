---
title: "Connecting 10.10 desktop to 10.10 server"
date: 2011-01-29
forum: Server Platforms
---

### Post by SteveTyrer on 2011-01-29
Hi all
I have had my Ubuntu 10.10 server running for about 4 months and i am very imprest, i connect to from my XP laptop using TightVCN, Putty and webmin. 
I have now installed Ubuntu 10.10 desktop on to my laptop and again its very good, **BUT** i can see all the files on the 10.10 server but i can not get *TightVCN, Putty and webmin* to connect to the server. i have tried setting up a new user but can not get things to work, can it be that i have a SAMBA server running on the machine i am trying to connect to?
now at a complete loss :-)

Steve

---

### Post by kill4killin on 2011-01-29
My first question would be if you are connection to the server from inside the network or from outside the network. If you are inside, confirm that the services are running on the server as you expect them to and verify that you are choosing the right ports and have not set any firewall rules on the server side.

If you're connecting from outside your network make sure that you have the ports you need forwarding on the router properly. One thing to note as well is that I have noticed my ISP blocks port 22 which you would normally use for ssh with putty. If you can get everything but this working try setting openssh on the server to listen to a different port.

As far as generic trouble shooting, make sure you can telnet to the server on the different ports your services are running on, if that works then it might be a misconfiguration with the program you're using on the laptop. Hope that helps.

---

### Post by SteveTyrer on 2011-01-30
> **kill4killin said:**
> My first question would be if you are connection to the server from inside the network or from outside the network. If you are inside, confirm that the services are running on the server as you expect them to and verify that you are choosing the right ports and have not set any firewall rules on the server side.

If you're connecting from outside your network make sure that you have the ports you need forwarding on the router properly. One thing to note as well is that I have noticed my ISP blocks port 22 which you would normally use for ssh with putty. If you can get everything but this working try setting openssh on the server to listen to a different port.

As far as generic trouble shooting, make sure you can telnet to the server on the different ports your services are running on, if that works then it might be a misconfiguration with the program you're using on the laptop. Hope that helps.

Thanks for the response.
I am connecting inside my local network, my laptop is dual boot Ubuntu/XP, when running XP all works fine but when booted to Ubuntu i cannot connect via Webmin, TightVCN or Putty, so all services are running on the server???

Steve

---

### Post by ryannathans on 2011-01-30
can you access the internet on your ubuntu laptop? There may be some network issues.

---

### Post by SteveTyrer on 2011-01-30
> **ryannathans said:**
> can you access the internet on your ubuntu laptop? There may be some network issues.

Hi
Yes I can connect to the internet and see all the files and can up load and down load to the server from my Ubuntu laptop.
Added bit of info when connecting with Putty it looks like it connects then get then is thrown off (hope this is not a red herring) :-)
Steve
PS: sending this from the Ubuntu laptop

---

