---
title: "infected machine behind dhcp server"
date: 2006-05-19
forum: Server Platforms
---

### Post by erimar77 on 2006-05-19
I have a CentOS machine running DHCP and NAT though gShield.  I am getting reports from my ISP saying that machine is "infected" because it's trying to connect to known bot controller.  There's quite a few Windows machines grabbing DHCP addresses from this server, what would be the easiest way to find out which machine is infected without walking to each machine and scanning it for viruses/spyware.

thanks for any help you can give me..

---

### Post by ubuntu_demon on 2006-05-19
Try running netstat on the CentOS machine. 

to see all connections :
$netstat -an --inet

to see only active connections :
$netstat -n --inet

You might use grep to filter a specific IP out (for example the IP of the bot controller) :
$netstat -an --inet | grep *IP*

I don't know very much about netstat. But you can find more information here :

$man netstat

---

