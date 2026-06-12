---
title: "Interesting Firewall Logs"
date: 2009-12-20
forum: Security
---

### Post by teward on 2009-12-20
Got a question for you all.  My laptop is currently on my home network, not the on-campus network, and its detecting multiple connection attempts from "Samba (SMB)" from a Windows Desktop on the network, and the internal network IP address of 192.168.1.255 which isn't even configured for anything on the network.

Any reason that I should be worried about this activity?

---

### Post by lisati on 2009-12-20
AFAIK "255" is sometimes used as part of a network mask, rather than as part of a regular IP address. If I saw such an address in my logs, I'd be inclined to double check the firewall settings on my routers. I'd also check what machines were connected directly to my home network.

---

### Post by teward on 2009-12-20
I've checked.  The network's encrypted, with MAC address filtering, and the only systems on the network (its a Verizon FiOS TV and Internet network) are two HD cable boxes (so they can access the DVR), a Windows Desktop Computer, my iPod, and this laptop.  I checked the firewall settings as well.  On my computer's firewall, I've disabled access to Samba's ports.  If I have the router disable the service, will that affect network performance at all?

---

### Post by koenn on 2009-12-20
192.168.1.255 is a broadcast address (on a network with mask 255.255.255.0) - this means that packets with this address as destination, will be seen by all hosts on the network.  Some protocols use broadcasts to make hosts or services known (it's used in windows networking/ file sharing); dhcp uses it because it needs to communicate with hosts that may not yet have an address.

---

### Post by memilanuk on 2009-12-20
Looks like a broadcast address...

[http://en.wikipedia.org/wiki/Broadcast_address](http://en.wikipedia.org/wiki/Broadcast_address)

Don't think I'd be too worried about it.  If you want, set up wireshark and capture the packets and see whats sending them out.

Whoops, looks like someone beat me to it ;)

---

### Post by teward on 2009-12-20
alright, I'll consider the 192.168.1.255 the broadcast address.

what about the direct connection attempts from the Windows computer on my network?  any reason it should be trying to connect to me in the background processes?  I'm thinking spyware or a virus or something.

---

### Post by mazz0 on 2009-12-20
I'm no expert, but I'd imagine that's just Windows trying to discover Shares, no?

---

### Post by koenn on 2009-12-20
what do your logs say ?

---

### Post by teward on 2009-12-20
the logs are on Firestarter.  all it shows is the connection attempt's port, source IP, destination IP, and what service it is (Samba).

Would disabling this through the router's systems do any harm to the network?

---

### Post by teward on 2009-12-20
Also, would removing the samba package do anything to seriously damage my system?

---

### Post by cariboo on 2009-12-20
If you remove Samba, the Windows computers on your internal network won't be able to access shares on the system running Ubuntu, It can still access shares on the Windows computers.

When you remove Samba, either use the purge option with apt-get, or the completely remove option using synaptic.

---

### Post by teward on 2009-12-20
> **cariboo907 said:**
> If you remove Samba, the Windows computers on your internal network won't be able to access shares on the system running Ubuntu, It can still access shares on the Windows computers.

When you remove Samba, either use the purge option with apt-get, or the completely remove option using synaptic.

The security freak in me doesn't like sharing files except through SSH or sftp, so I have nothing shared on the network that could be accessed anyways by Windows

---

### Post by teward on 2009-12-21
Just a late followup.  I checked the packets with Wireshark, and I learned that my computer was sending out Samba packets to the multicast address, which explains the connection attempts.  Uninstalling Samba got rid of the issue.

---

