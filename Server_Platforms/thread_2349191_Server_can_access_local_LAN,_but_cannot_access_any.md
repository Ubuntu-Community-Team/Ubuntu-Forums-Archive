---
title: "Server can access local LAN, but cannot access anything outside of it"
date: 2017-01-12
forum: Server Platforms
---

### Post by chris399 on 2017-01-12
Hello,

I have two separate servers (i.e., two separate machines). They are both Ubuntu. Lets call them server 1 and server 2. They are both in the same lan with static IPs. They are connected to a cisco consumer switch and the switch is connected to a ubiquiti edge router lite. All was working well until I got a power outage. After the outage, I restart both servers. Server 2 is working fine. Server 1 cannot access anything outside of the local lan and cannot be accessed from outside of the local lan. More specifically:

Server 1 can ping server 2. 
Server 2 can ping server 1. 
Server 1 can ping the router. 
The router can ping server 1. (I was able to do this because the ubiquiti router has a cli interface). 

But

Server 1 cannot ping any address outside of the lan. I have tried with ip addresses and domain names, neither works. 
Computers outside of the lan cannot ping server 1. I also cannot ssh to server 1 from outside of the lan. The behaviour is like a firewall -- i.e., you get no response when you try to ssh instead of a message that says "connection refused."

At first I thought that some firewall had sprung up somehow. To test this, I took a windows laptop, configured it with the static ip of server 1, unplugged the ethernet cable from server 1, and plugged it into the laptop. Surprisingly the laptop worked fine. It could ping everything, access the internet, etc. So there does not seem to be a firewall problem. 

The problem is with server 1, somehow. What is wrong? Can anyone help?

---

### Post by darkod on 2017-01-12
I assume you don't have firewall active on the server, right? Because depending on settings that could block all traffic, including outbound.

I also assume you double checked network config (if it works on the LAN it should be good, but it doesn't hurt checking it). Also, just in case, can you try another port on the switch? I know the laptop worked with the same cable, but still just in case try connecting the server to another port on the switch. Or even to the router directly.

Any MAC filtering you are using somewhere in the LAN? MAC filter would block that device but would allow another device on the same cable/port.

---

### Post by chris399 on 2017-01-12
Darko, thank you for the response, 

I do not think I have a firewall active. I do not really know how to set up a firewall on cli linux. But I will try to look it up and check if there is one active. But a firewall wouldn't block remote connections and leave local ones undisturbed would it? I already thought of the different ports of the switch attempt. I did that, there was no effect. The working server kept working and the broken one kept ignoring remote connections while working fine on the LAN. It is not possible to connect directly to the router, the switch and the router are in different rooms, and I do not have a cable long enough. 

I do not think I am using mac filtering. I am not that advanced in networking and I would not set something like this up. I do not think the CIsco consumer switch is capable of mac filtering (is it?). And as for the router I checked its settings and there does not seem to be anything like this set up. The router's firewall is off. 

I checked network config, and as far as the stuff I understand goes (i.e., ip address, gateway, netmask, dns servers) everything seems to be correct. But I am not sure about more advanced network config (i.e., routes, etc). Could this be a problem? How can I make sure my routes are correct?

---

### Post by chris399 on 2017-01-12
So I did:

sudo ufw disable

on server 1, and there is no change in behaviour.

---

### Post by darkod on 2017-01-13
Sorry, but I am puzzled too. You can see the routes configured with:
```
route -n
```

In theory it should simply work. But you obviously have some problems either with this server installation (maybe something corrupted) or some conflict in the network.

---

