---
title: "Ubuntu dhcp server wont give out ip"
date: 2012-06-06
forum: Server Platforms
---

### Post by Burny17 on 2012-06-06
I am new to setting up servers and have tried setting up a dhcp server 4 times and i have tried several guids. I have the same problem everytime i  try making a server dhcp.  The server setup vas sucsessfull and every thing seems to be right but i still dont get a new ip on the client computer. is there a command or somthing i have to use for the server to give out ip`s?

---

### Post by SeijiSensei on 2012-06-06
First, make sure there's no other DHCP server on the network, like your router for instance.  Then watch the Linux DHCP server's log with "tail -f /var/log/syslog" while you restart the network on a client machine.  If you have Windows clients, for instance, you can issue the commands:

Windows commmands:
```

ipconfig /release
ipconfig /renew

```

at a Windows command prompt.  Does the server log the broadcasted DHCP request?  Does the server reply?  If not, what errors does it throw?

---

### Post by Burny17 on 2012-06-06
i did not get a new ip it showed up as 0.0.0.0 
it cant connect to the dhcp server or cant find it. it is connected via a cable directly with the client

---

### Post by SeijiSensei on 2012-06-06
You have two computers connected together with a standard Ethernet cable?  That won't work.  You need either a special cable called a "crossover" or you need to connect both devices to an Ethernet switch or hub.  

(With a regular cable, the transmit pair on the two computers are connected together as are the receive pairs.  Thus when one machines "talks" the other cannot "hear" it.  A crossover cable connects the transmit pairs on each end to the receive pairs on the other so the machines can communicate.)

I'd buy a [cheap switch]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833166035") in case you want to expand your network someday.

---

### Post by Burny17 on 2012-06-08
I now have a switch connected but stil no contact with the dhcp server

---

### Post by SeijiSensei on 2012-06-08
Why don't you start with a simple [static IP]("http://www.cyberciti.biz/faq/ubuntu-static-ip/") configuration on each machine?  Put them both in the same subnet, say 192.168.1.0/24.  Once you can get the two machines to communicate, you can starting to deal with DHCP.

Also I'd check to make sure that you didn't connect one of the machines to the "upload" port on the switch.  You want to use any ports but that one.  It's designed to connect to another switch.

---

