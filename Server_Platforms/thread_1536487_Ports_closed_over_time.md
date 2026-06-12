---
title: "Ports closed over time"
date: 2010-07-22
forum: Server Platforms
---

### Post by Emascu on 2010-07-22
Hello.

I'm trying to run a web server on ubuntu lucid, and I have a problem what is not directly linux related, but a problem with opening ports. I hope this question is welcome here as well. When I open port 80 everything works well. My server is accessible from outside. But strangely the day after the port is closed again. Right now I have do reset my router every day to keep that port open and well, that's not much of a solution.
I wonder how it is possible. I configure everything on my router, I save the settings and it works. How come it automatically resets my configurations over time? any idea?

Thanks,
Emass

---

### Post by cdenley on 2010-07-22
I'm guessing by "opening the port" you mean configuring a port forwarding rule in your router? When the port is "closed" the next day, is it because the router is no longer forwarding the port, it is forwarding the port to the wrong LAN IP, or the connection is not accepted by your server?

---

### Post by Emascu on 2010-07-22
> **cdenley said:**
> I'm guessing by "opening the port" you mean configuring a port forwarding rule in your router? When the port is "closed" the next day, is it because the router is no longer forwarding the port, it is forwarding the port to the wrong LAN IP, or the connection is not accepted by your server?
By opening the port I mean forwarding in my router to the LAN IP of my server computer. I'm pretty sure it's the right LAN IP (192.168.1.3). I'm not sure either the connection is accepted by my server.
But the strange thing is, it is working after the reboot of the router after I saved the settings to it. 
The only thing I can think of is that the 'quick' way I'm doing it now is not working. By the 'quick' way I mean that there's an option in my router where I can add the ports for a web server and it should work. A little hard to explain but I guess the image below will clear it up.



Maybe it's just not working this way and I have to do it through 'Custom Port Forwarding'. But I've entered every combination of IP addresses and source/destination IP addresses but nothing seems to work. So I made a screenshot and maybe anyone here can tell me how to open port 80 correctly? This is how it looks like on my router.

---

### Post by cdenley on 2010-07-22
When it stop working from outside your network, can you still access the server by browsing [http://192.168.1.3/](http://192.168.1.3/) inside your network? Are you sure there isn't an IP conflict? Have you assigned any IP's manually? Do you have another device such as another router which may be acting as a DHCP server?

---

### Post by Emascu on 2010-07-22
> **cdenley said:**
> When it stop working from outside your network, can you still access the server by browsing [http://192.168.1.3/](http://192.168.1.3/) inside your network?
Yes, that still works. That never stopped working. And when port 80 is 'open', I can acces my LAN IP inside my network.
And no, I have not added any IP's manually and there's no DHCP server. Just Apache and an FTP server.
I do have an other switch on the network, but that one is to boost the wireless on the other side of the house and my server computer is not connected to it.

---

### Post by cdenley on 2010-07-22
> **Emascu said:**
> And no, I have not added any IP's manually and there's no DHCP server.

Well, if you have no DHCP server, then you would have to be assigning IP's manually, or else they would have none. I would assume your router has a DHCP server.
> **Emascu said:**
> 
I do have an other switch on the network, but that one is to boost the wireless on the other side of the house and my server computer is not connected to it.

Are you sure that "switch" doesn't have a DHCP server which is assigning IP addresses which conflict with IP's assigned by your router?

---

### Post by Emascu on 2010-07-22
> **cdenley said:**
> Well, if you have no DHCP server, then you would have to be assigning IP's manually, or else they would have none. I would assume your router has a DHCP server.


Are you sure that "switch" doesn't have a DHCP server which is assigning IP addresses which conflict with IP's assigned by your router?
I must admit I have little knowledge about DHCP servers and which IP conflicts with what IP.
I do have the box of the router (not the switch), and the box tells it has a 'DHCP client/server'.
And I'm not sure but the switch may have a DHCP server as well, but can that be a problem even of my computer is not connected to it? And what can I do about it?

I do really appreciate your quick help! :D

---

### Post by cdenley on 2010-07-22
> **Emascu said:**
> I must admit I have little knowledge about DHCP servers and which IP conflicts with what IP.
I do have the box of the router (not the switch), and the box tells it has a 'DHCP client/server'.
And I'm not sure but the switch may have a DHCP server as well, but can that be a problem even of my computer is not connected to it? And what can I do about it?

I do really appreciate your quick help! :D

Well, if the two devices are on the same network, and they're both assigning addresses for the same network unaware of what the other is assigning, then two computers will inevitably end up with the same IP address. If two computers are using the IP 192.168.1.3, how is your router supposed to know which one to "port forward" to?

If this is your problem, I can't tell you how to fix it, because I don't know how your network is configured.

---

### Post by Emascu on 2010-07-22
Ah I see. I checked every computer in the house and each computer has it's own unique LAN IP, so I guess that's okey.

Can you help me with filling in these fields? because whatever I try to fill in, the ports stay closed.

---

### Post by cdenley on 2010-07-22
With DHCP, IP's do occasionally change. Your regular port forwarding should work fine.

connection: I don't know
source IP: 0.0.0.0 (I guess)
source netmask: 0.0.0.0 (means everything)
destination IP: 192.168.1.3 (your server's IP)
desintation port start: 80
desintation port end: 80
desintation port map: 80

Does your "switch" have an IP? What is the LAN IP of your router?

---

### Post by Emascu on 2010-07-22
Okey thank you very much. It seems to be working now, let's see how it'll do tomorrow!

Thanks for your help, cdenley!

---

