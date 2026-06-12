---
title: "After long period of time make pc wake up with connection rj-45"
date: 2016-11-19
forum: Server Platforms
---

### Post by sed_faster on 2016-11-19
Hello folks

I have an ubuntu server 16.04 lts headless. I intended to connect with this pc through ssh, via rj-45. I though that necessary cable crossover, but do not need anymore. I use a normal rj-45 cable. But when I connect my laptop directly on the ubuntu server, after headless a long period anyone access them and after I set my port network with correct ip and gateway I can not establish connection between pc's.

I need to put, between pc an router and access through them. Or reboot ubuntu server to establish connection with my laptop through only rj-45. But I could not reboot my ubuntu server, I could not get my way: P

How to set ubuntu server to any pc with connection via rj-45 with ip address correctly be likely ignite it through ssh?

thanks

---

### Post by cariboo on 2016-11-19
I've never connected to another computer with a direct cable connection, but make sure that the ip addresses aren't the same and that they are both in the same subnet. I use two routers and a switch for my network, and can connect to any other system on the network using ssh and sftp, no other protocols needed.

---

### Post by sed_faster on 2016-11-23
After login server I can connect direct through rj45, only! But if I try this after three days the lost server connection and my pc can't establish connection with server through cable rj45. I have to put router btween my pc and server to rj45 connection in server wake up and I can establish connection.

Any idea how can I solve this?

Note: If my english it is very wrong, please tell me! I will try explain again. My level English it isn't very good but I will try, I promised :)
thanks

---

### Post by sully101 on 2017-01-02
Hi Edgar,

You need wakeonlan installed on client to wake your server by mac address. From memory the server also needs an option in the /etc/network/interfaces file to set the interface to accept wake on lan packets after shutdown. Your BIOS may have a setting also. If the server is loosing its network settings on reboot then look into configuring the network through the /etc/network/interfaces file. If you need to connect any client to your server and be able to ssh into it ( really bad security ) then you should probably have a DHCP server running on it. Two DHCP servers on one subnet is a pretty bad thing.

---

