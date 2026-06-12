---
title: "ufw"
date: 2013-11-23
forum: Security
---

### Post by clearski on 2013-11-23
Hi, everyone!

I was taking a look at the firewall log this morning and I noticed a strange event:

```
 Nov 17 17:12:42 <hostname> kernel: [  793.277761] [UFW BLOCK] IN=eth0 OUT=MAC=[macaddress]  **SRC=[external-IP-address]** **DST=[private-IP-address]** LEN=54 TOS=0x00 PREC=0x00 TTL=108 ID=[somenumber] **PROTO=UDP** **SPT=[high-port-number] DPT=[high-port-number]** LEN=34
```

It seemed that somene using an external IP tried to reach a private IP address. I am not sure if that happened using an already established connection? The first part of the [macaddress] was the address of my NIC, followed by some a string that I couldn't link to anything local.

 It's the first time I am seeing this, so is there any reason to raise eyebrows?

---

### Post by bashiergui on 2013-11-23
If the private ip was 192.168.x.x then you can post it without worry. Seeing the port numbers would help. But the connection was blocked so what is the worry.
Or you can research it yourself by googling the source and dest ports and IPs. Determine who owns the IPs and what services commonly run on those ports.

---

### Post by clearski on 2013-11-24
Thank you.

I did a lookup on the IP, it came from the States, but it doesn't really matter where it came from. :) But I didn't google for that IP and the port...

I cleared the log since the attempt was blocked anyway, but I was wondering how did he use a connection to try to access the private IP it originated from. That's interesting.

I also discovered that the second part of the [MAC] was 90% of the router's hw address and the last four or six numbers I couldn't link with anything else.

Since I am not keeping a record of visited sites I cannot leave a bait to find out more, my guess is that it was related to a http connection. Who knows...

---

### Post by bashiergui on 2013-11-24
It does matter where it came from if you're worrying about it. If it is Google's IP then there are no concerns. If it's from some dubious country and is owned by a blacklisted party then it might have been malicious. If it's port 80 then it's probably from a browsing session. if it's port 4444 then it's slightly more interesting. But your firewall blocked it so it isn't concerning either way.

Your router has a public IP externally and it keeps track of your internal private IPs inside of your LAN. The reason your ufw log shows the destination to be the private IP is because the router recognized your computer was the intended recipient and translated your public IP to your private IP.

He did not use a connection. There was no connection because the packet was blocked by ufw.

---

### Post by clearski on 2013-11-24
Just for theory... why would it be fine if it came from Google, but it would be wrong if it came from China? If someone tried to hijack a connection, to me there is no difference.

Yes, the router has a public interface and an internal one and keeps track of the local addresses from which start the requests to remote hosts, and then directs the reply packets back to the same internal host from which they sent... but 99.9 of the packets are not blocked by the firewall and do not appear in the logfile... so what exactly happened with this packet that was different and was blocked?

---

### Post by bashiergui on 2013-11-24
There is a huge difference. Surely you can see that.
There was NO CONNECTION. The firewall blocked the connection.> **clearski said:**
> so what exactly happened with this packet that was different and was blocked?No one can tell you that with what you have provided. I encourage to research it yourself or post more information. 

good luck to you.

---

