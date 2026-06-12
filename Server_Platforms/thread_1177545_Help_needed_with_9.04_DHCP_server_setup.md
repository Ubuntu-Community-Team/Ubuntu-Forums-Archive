---
title: "Help needed with 9.04 DHCP server setup"
date: 2009-06-03
forum: Server Platforms
---

### Post by NoMeansNo on 2009-06-03
Hey guys/gals

First off let me preface this by saying just by poking around in the forums here for a bit it is clear you guys have the best user community for any Linux distro and maybe even the 'net in general. I have messed around with Ubuntu in the past (6.04 was the first I recall playing with) but am still a noobie. That said, I thought it would be a fun project to install a DHCP server on a desktop install of 9.04 since I dont have any extra routers laying around but I do have a desktop to use.

The actual utility for this is as follows: Every other week myself and group of friends do an Age of Empires II LAN at my house. I'm the "tech guy" with the switch so I get the job of figuring out how to make it all work. I intend to setup a DHCP server in Ubuntu to handle to task of assigning IPs to all machines plugged into an 8-port switch. I dont want these machines to be online or anything, this is just a LAN for strictly gaming.

So far I've followed this random guide I found online: [http://taufanlubis.wordpress.com/2007/10/14/dhcp-server/](http://taufanlubis.wordpress.com/2007/10/14/dhcp-server/) but am unable to get the server actually up and started.
My questions are as follows:

1.If I'm not going online do I need to specify DNS servers?

2.What does the status of the IP need to be for the desktop that is acting as the server? Does it have to be static or something?

3.How do I specify which ethernet port will be the one plugged into the switch assigning the IPs? I have 2 onboard NICs and one wireless card. All of which Ubuntu installed beautifully.

I can post the contents of my dhcpd.conf if that will help at all.

---

### Post by puppywhacker on 2009-06-03
If all you want is to assign ip addresses you have to set an ip address on your internal address first (static is highly recommended for a server) and based on the netmask this address is matched against the subnet in your dhcpd.conf. this means that if your ip-address is not set when the dhcp server is started everything will fail.

the random page has good instructions. The most important thing for you to set is the subnet. So imagine you are using 10.0.0.1 for your server, your clients will then have ip-addresses between .10 and .20

```
subnet 10.0.0.0 netmask 255.255.255.0 {
  range 10.0.0.10 10.0.0.20;
} 
```

if you don't need name resolving or routing you don't need to change anything else.

---

### Post by Iowan on 2009-06-03
[Here]("http://www.crazysquirrel.com/computing/debian/servers/dhcp.jspx") is an interesting How-To I found whilst looking for info on binding to a specific interface.

---

### Post by NoMeansNo on 2009-06-03
Wow thanks guys these are both super helpful. I'll report back tomorrow afternoon with results.

---

### Post by NoMeansNo on 2009-06-04
The DHCP server is up and running and I have confirmed its able to assign IPs to various machines through my unmanaged D-link switch. Also I created a game in AOEII on one machine and was easily able to join with the other. The problem we occasionally have while running AOEII is that the game stutters and lags dude to some kinda network problems. This is usually apparent in the first few minutes of play so I tested it out. Preliminary results were promising and showed no issues.


I have a few more questions: Is there anything I can add/remove/alter in my conf file to optimize this setup or make it more foolproof? Here it is in its entirety:

```

ddns-update none;

default-lease-time 600;

max-lease-time 7200;

subnet 10.0.0.0 netmask 255.255.255.0 {

range 10.0.0.10 10.0.0.20

}

INTERFACES="eth0";
```

Since I have no intent to connect to the internet, does it matter that the Windows clients don't have an IP for the default gateway? 

Additionally, is there a way I can setup this machine so I can plug it into an outlet in a corner, run my cat5/cat6 cable from its Ethernet interface (eth0) and have it start the DHCP daemon without any interaction? I know I can just setup auto login but what else is needed?

---

### Post by puppywhacker on 2009-06-04
As a very small comment, I would increase the default-lease-time to 18000 (5 hours) and the max-lease-time to 36000 (10 hours) This will prevent the clients from renewing their ipaddress every 5 minutes.

you don't need a default gateway unless an application wants to talk to anything else than 10.0.0. ... maybe an application on the windows clients require an internet link?

to start up application go to "system / administration / services" and make sure the dhcp server is marked,

this should be equivalent to making a softlink of the dhcp3-server init script to the rc3 (or is it rc5?) 
```
ln -s /etc/init.d/dhcp3-server /etc/rc3.d/S40dhcp3-server
```

---

### Post by NoMeansNo on 2009-06-05
Implemented all of your suggestions. I will be playing tonight with friends and will let you know how it goes. Thanks a bunch for all the help!

---

### Post by NoMeansNo on 2009-06-09
Sorry for the few days delay. Got caught up other pursuits. Everything worked FLAWLESSLY Friday, no issues with lag, not being able to join games or anything else. I will definitely be utilizing this setup going forward. Thanks a bunch for all the help everyone.

---

