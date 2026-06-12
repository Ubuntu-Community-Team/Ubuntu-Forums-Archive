---
title: "problem accessing internet"
date: 2010-11-24
forum: Server Platforms
---

### Post by upstatelabs on 2010-11-24
Hi.  I am having a network access problem that I just can't figure out.   I'm running server 10.04 and I can only connect to the internet  intermittently.  I have no trouble internally, and I can ping the  gateway and other server, and see other computers.  The other computers  can access my samba files and are using the forwarders I configured, and  can get to the internet, no problem.   If I try to up/download a file  from the internet, it will usually start, but then freeze; it might  finish at some point, but often not.  I can't use apt-get to update, it  just fails to download.

This server was working just fine for over a year, and then out of the  blue, this.  I don't know what to check, or even if there is a log file  that might help.

---

### Post by arrrghhh on 2010-11-24
Hm... if local traffic is fine, then your NIC and server are most likely fine.

Also, if you can access the internet *somewhat* I would think your config would be fine as well.  Has anything changed with your provider?  Are any other machines using the same pipe (network connection) to get out to the 'net?

---

### Post by Rusty au Lait on 2010-11-24
There's just too many places to start. What is the DSL/cable modem you are using, if indeed that is your access to the internet? Assuming your samba access is restricted to a local network, what is your gateway and/or firewall setup to the internet. If this is a recent problem what changed in your system? If you can't even get updates from ubuntu I have to suspect the ISP connection.
Sorry, that's all I've got for now.

---

### Post by aromo on 2010-11-24
Do a traceroute to an Internet IP address (e.g. 8.8.8.8 <= Google's DNS server) while it works and save it to a text file.

When you experience the problem, do the same and compare the text files.  You should be able to determine where you're losing your packets.

---

### Post by upstatelabs on 2010-11-24
Thanks all for your responses.

First, I'm pretty sure I don't have a problem with my provider.  All of my other systems (windoze,linux) all work fine. 

Next, I should say, that I'm not using 10.04, but 9.10 (sorry).  I did upgrade from 9.04 to 9.10 awhile back, but I didn't notice any problems at that time.  The only other changes that I can think of is regular ubuntu updates.

I can't traceroute because I don't have it installed, and I now can't install it (apt-get fails to get files).  I can't ping 8.8.8.8 (times out).

---

### Post by upstatelabs on 2010-12-02
Hi all.  I am wondering if anyone else might have any ideas on my  problem 9.10 server that has full internal network access, but not the  internet. 

I have many boxes on the network that have internet  access, and my smoothwall firewall doesn't have any special settings for  the server that are different from the other machines.  I tried  tweeking my bind and resolv.conf settings to no avail.  There must be  some setting I haven't thought of.  :sad:

Thanks!

---

### Post by HugoSerrano on 2010-12-02
Can't see what may be happening. You got internal access, external access its messy, all others LAN machines access WAN with no problem.

Change network cable, check internal routers/switchs, change switch ports.

---

