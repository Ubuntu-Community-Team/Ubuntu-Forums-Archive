---
title: "Any way to remotely get IP of server running on LAN?"
date: 2006-11-21
forum: Server Platforms
---

### Post by SDREnate on 2006-11-21
I have a Counter-Strike server running Ubuntu 6.06 that I primarily use as a LAN server. I use puTTY and WinSCP3 to remotely administer to it from my Windows box. Currently, to get the IP of the server I have to have a monitor and keyboard attached to it so I can get the IP using 'ifconfig'.

Is there any way to get the IP of the server from my Windows computer? My current situation works, but I'd rather not have to drag the monitor along when I take the server to a friends house to play CS.

I've tried google and searching the forum, but I haven't been able to find anything helpful. I've seen other people ask this question on this forum before, but I've really never seen a decent answer.

---

### Post by Jimmey on 2006-11-21
Can you make the IP static?

[Edit]

I think that you can use the computer's hostname to connect to. Might be wrong though. Let me check this out a bit more.

---

### Post by SDREnate on 2006-11-21
> **Jimmey said:**
> Can you make the IP static?I'm not sure. The address is assigned by DHCP. Unless there's a way to assign static IPs in the router setup, I'm not sure how to do that.

---

### Post by Jimmey on 2006-11-21
When you go round to your friend's, it's basically a LAN party?

What does the network look like when everythings hooked up?
And how many network interfaces do you have?

---

### Post by bmillsap on 2006-11-21
Can you find it from your friend's (or whoever's) DHCP server?  In my Linksys router, you can get a list of current DHCP clients, and if the client passed a hostname, it shows it also.

---

### Post by tturrisi on 2006-11-21
or just use a network scanner on the net that the comp is connected to at the time to see all hosts on the lan.
windows freeware scanners:
[http://www.snapfiles.com/Freeware/network/fwscanner.html](http://www.snapfiles.com/Freeware/network/fwscanner.html)

---

### Post by blackmh on 2006-11-21
Find out servers MAC address (ifconfig eth0)and write it down. Then, when everything is hooked up, server should be broadcasting things over the network. Open command prompt on windows machine and enter "arp -a" and one of entries should be MAC address of server with it's actual IP address. 1 min of work...

---

