---
title: "New to sniffing network traffic"
date: 2008-03-22
forum: Security Discussions
---

### Post by empthollow on 2008-03-22
I am trying to sniff packets on my home lan.  I have discovered dsniff & company utilities but have yet to get the to accomplish my task.  I have tried 
```
urlsnarf -i eth1 
```
but it seems to sniff traffic only on the machine that i run it from.  I've done some reading and from what i understand i need to use the arpspoof utility first.  I have tried this.
```

# echo 1 > /proc/sys/net/ipv4/ip_forward
# arpspoof -t target host
# aprspoof -t host target
```
All wend well until the last command where i go the response
```
arpspoof: couldn't arp for host 192.168.2.4
```
so i tried to urlsnarf -i eth1 without the last command and again got traffic only on the machine i ran it on (host).  I am having a hard time finding any additional info on how to use these tools in these forums or anywhere on the net.  Any help would be appreciated.  Thanks.

---

### Post by kevdog on 2008-03-22
Take a look at a product called wireshark.

---

### Post by empthollow on 2008-03-22
i tried wireshare but it doesn't seem to pickup http traffice from another machine either.  I can see nfs and some other protocols but not urls.  Unless you have some expierence with wireshark, i'd be happy for some further input.

---

### Post by empthollow on 2008-03-22
ok, i maybe jumped the gun on no http traffic.  It shows me http traffic but again it only shows it from my host machine i.e. the machine i run it on.

---

### Post by kevdog on 2008-03-22
So you need a wireless card (if you are sniffing wireless) that you can put in Infrastructure (or AP) mode.  Is that what you want to do?

---

### Post by empthollow on 2008-03-22
Well, my setup is that i have 2 wired computers and a wireless laptop.  This is all being distributed by a belkin wireless router which has 4 ethernet ports.  i'm trying to sniff traffic on a wired computer.  I have tried the wireshark and arpspoof methods from a wired computer and from my wireless laptop and got the same results from both.

---

### Post by picopir8 on 2008-03-23
The fact that you are only seeing traffic for the wired machine is normal.  It is behind a router with a build in switch which will filter out all traffic not destined for that machine.  If you want that machine to see all traffic then you will need to replace the switch with a hub or move the wired computer elsewhere on the network where the traffic is not filtered (ie other side of the router).

---

### Post by kevdog on 2008-03-23
Yes, you would put your computer in front of the router or switch and make a network bridge to monitor the packets as they passed through.

---

### Post by empthollow on 2008-03-23
ahh, i see, thanks for the feedback.  I just found out today that i can view all traffic on my network if i use ettercap to spoof.  I'm glad i found a way to make it work but i'm also interested in why it works.  Does anyone know why ettercap can capture all traffic and arpspoof does not.  i still need to use urlsnaf and such to view the traffic but ettercap redirects it.

---

### Post by cdenley on 2008-03-24
I never used arpspoof before, but judging by the name, it uses the same attack method. It is called a man-in-the-middle attack. Switched networks rely on the ARP protocol to match MAC addresses to IP addresses, since switches only see MAC addresses. Your computer tells the target that you are the gateway, and tells the gateway that you are the target. This is called ARP poisoning/spoofing. You then have to route the traffic between the target and gateway, so the target can connect to the internet and receive replies, but it will all be routed through you.

I'm guessing what you were doing before didn't take care of the routing that had to take place. Be careful when playing around with ARP poisoning. I accidentally crashed a network once doing this.

---

### Post by empthollow on 2008-03-25
I'll heed your warning, from what i've read it seems that a graceful shutdown of the spoofing program is key.

---

