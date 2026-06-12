---
title: "need some experienced help please"
date: 2007-12-27
forum: Tennessee Team - US
---

### Post by thrownintothis on 2007-12-27
Here’s a somewhat detailed description of the current setup we have.

 

In the apartment building, there are 8 floors. Only floors 2 through 8 have internet access, 1st floor only the managers office has internet access and it gets a static IP.

 

Floors 2 through 8, every apartment has a wired LAN connection, and there are 3 wireless AP’s on each floor (Mikrotik 2.4GHz) 

The server is on the 5th floor, there are switches located on every floor, north end of the building and south end.

Each AP has a static IP on it presently, basically for remote monitoring and remote access. Each AP has DHCP running on it as well and have 192.168.x.x IP’s on them. The server (running ubuntu) has dhcp3 running on it with 1 full class c block setup on it. IP tables are also running on the server and things are setup that you can only sh into the server from specified IP’s or you have to be sitting at the server itself. Each tenant of the apartment complex should be able to access the internet via a wired connection in their apartment or via one of the wireless AP’s

 

I just had 2 cable services installed at the location, 8 megs each, in order to replace a 10 meg wireless link that was serving the building. I do know that, although each of the cable services installed have 5 static IP’s assigned to them, the SMC router/cable modems do DHCP as well and assign 10.x.x.x IP’s to each user. On one service, I plan to assign 1 static to the server, and 1 to the managers office. I plan to add another NIC to the server (giving me a total of 2 NIC’s) and assign a second static IP to that NIC. 

 

I believe I need to shutdown the DHCP3 service currently running on the server, then change the IP tables to allow access using IP’s from the cable company. I’m really new to the linux/ubuntu OS and need some guidance. All is appreciated. If anyone needs any other information, please let me know.

I have been chatting via email with one guy and here is what he say's.....
You are stuck. You can't do that and bond/load balance those connections.

You have to (this will look ok in a fixed font):

   Comcast1          Comcast2
     \                /
      \              /    Public IPs - (DHCP'd or not)
       \            /
   [ Linux boxen upstream nic              ]
   [ iptables, squid, dansguardian, DHCPD, Load Balancing Routes  ]
   [ Linux box downstream nic              ]
          |
          |
          |
     [switch/hubs]

     /       \         \            \

WiFiAP1    WiFiAP2   Dorm Room    Dorm Room


---------------------------

This is a lot more than any sane person wants to do on a system from remote. Too many variables.

I don't have time to train you and/or babysit this kind of thing for a while. Can you find a local linux/tcpip networking dude?

I'm lost, know very little about this stuff, and I have GOT to get these changes made before Jan 4th. Can anyone help me?

---

### Post by tenhuseegeek on 2008-05-06
Sounds like a big undertaking, but if you do this one stage at a time it should be ok, first of all I see you have way to many dhcp servers in the mix, all the wireless ap's should be disabled for dhcp and let the server do this for you, then you can manage the scope better. I have heard that you can use dual nics in linux and bond them to get full bandwidth (100Mbs x 2 = 200Mbps). I would statically set ap's keeping an eye on each set. Floor 1 ap1=x.x.x.20, ap2=x.x.x.21, etc. Install bind9 and dhcp3 on server. If you have 2 cable connections coming in to server, you will/may want to add 1 or 2 more nics in server and use these for your lan connections to switch (other 2 for broadband connections). 

Get this all working first, then takle squid and dansguardian, both of which i run at home (they work great by the way).

```

Cable----nic1--          -----nic3--         |------ap1 (nodhcp)
              |         |           |        |------ap2 (nodhcp)
               > Server               Switch-|------ap3 (nodhcp)
              |   dhcp  |           |        |----workstation
Cable ----nic2    bind   -----nic4--

```

I hope I am understanding you properly, if you need help with bind9 and dhcp3, I can help you there too, also install Webmin, it is great for configuring this stuff.

If you run you server directly to cable connections, PLEASE install fail2ban and iptables (PROTECT YOURSELF!). Please keep in touch and let me know how goes it.

Repost - diagram didn't work, also attached.

---

