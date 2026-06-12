---
title: "Access via Putty"
date: 2008-09-15
forum: Server Platforms
---

### Post by vegas588 on 2008-09-15
I am a newbie trying to learn Ubuntu Server. So far, I have been having alot of success and I am enjoying the learning process. However, I can only access the server via the terminal on the server itself. I have been trying to use Putty to access it via SSH from my Windows desktop, but the connection times out every time and does not even get to the point where I get a prompt on the Putty screen.

I installed the openssh-server via this command:
sudo apt-get install openssh-server

the server has a static ip address

What am I doing wrong?

---

### Post by hrod beraht on 2008-09-15
Do you have a router? If so, are you forwarding the SSH port through your router to the static IP address of the server? If not, the SSH request will never get past the router.

Bob

---

### Post by vegas588 on 2008-09-15
We do have a router. I don't see why the request would go through the router because my desktop is on the same lan as the server.

---

### Post by vegas588 on 2008-09-15
excuse me, I should have said subnet, not lan!

my desktop is on the same subnet as the server.

---

### Post by vegas588 on 2008-09-15
Interesting, I just realized that I cannot even ping the new Ubuntu server. Some kind of default security that would stop that? I gave the server a static ip and set the correct gateway. I can ping out from the server to any ip address local or remote.

---

### Post by vegas588 on 2008-09-15
OK. Problem was related to the fact that the ip address changed. I can connect now.

So, I guess the question turns to this: How does one set a static ip address on ubuntu server? I used the command: sudo ifconfig eth0 x.x.x.x. netmask x.x.x.x

and sudo route add default gw x.x.x.x 

Rebooted and it went back to DHCP

How do I remove DHCP?

---

### Post by The Cog on 2008-09-15
First, check the port is open on the server. List the listening ports with this command:
**netstat -ltn**
and make sure you can see an entry for either :::22 or 0.0.0.0:22. If not, the server isn't listening.

Second, see if you can telnet the server from the client with this command (use the correct IP address for the server of course):
**telnet 1.2.3.4 22**

---

### Post by The Cog on 2008-09-15
Ah. that bit's easy. 

First, you should also look at the contents of /etc/resolv.conf while you are on DHCP, to see what the name server configuration should be. You may need to replace the config manually once DHCP is not doing it at boot-up.

Second, edit /etc/network/interfaces. Comment out the line about DHCP and replace it with the static config details. 
Here is an extract from my file /etc/network/interfaces as an example:
> iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1


---

### Post by vegas588 on 2008-09-15
I found that file and you are correct, it is set to dhcp. I will need to change that, however the file is read-only. So, I need to change the permissions first. I am not sure exactly what permissions I will need. I will need to look that over. 

Good learning!!

---

### Post by hrod beraht on 2008-09-15
> **vegas588 said:**
> ...the file is read-only. So, I need to change the permissions first. I am not sure exactly what permissions I will need.


You don't need to (and shouldn't) change the permissions of the file. Simply use *sudo* to temporarily become superuser and edit the file. As in:
```
vegas@myserver:~$ **sudo nano /etc/network/interfaces**
```

Bob

---

### Post by vegas588 on 2008-09-15
OK I correctly set my eth0 to static and gave it the appropriate network addresses. What do I need to edit in the name server "resolv.conf" file to set up my dns server settings?

Can you give me an example like the one for your ip settings?

---

### Post by cariboo on 2008-09-16
Your dns settings in resolv.conf should be the same as the dns seetings on your router but they should be set automagically when you're connected to the network. At least that's they way it worked with my server.

Jim

---

### Post by The Cog on 2008-09-16
Oh ****!

I missed a line from interfaces. Here is the corrected sample with the added line:
> auto eth0
iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1


resolv.conf gives the name servers. In my case my router actes as a DNS proxy to the real DNS servers in my ISP, so it looks like this:
> nameserver 192.168.1.1

---

### Post by Viruk on 2008-09-16
I don't know how much difference this will make to you, but I have some slightly different lines in /etc/network/interfaces

The IPs below are just an example and should be changed to suit your network.

auto eth0
iface eth0 inet static
	address 192.168.0.10
	netmask 255.255.252.0
	network 192.168.0.0
	broadcast 192.168.3.255
	gateway 192.168.0.1

---

