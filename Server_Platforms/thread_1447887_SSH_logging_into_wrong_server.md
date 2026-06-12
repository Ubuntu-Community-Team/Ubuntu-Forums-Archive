---
title: "SSH logging into wrong server"
date: 2010-04-05
forum: Server Platforms
---

### Post by rpgsimmaster on 2010-04-05
I'm having a problem with SSH (and other services) intermittently logging into the wrong server from some clients.

The setup is this: I operate a fileserver with one NIC with an IP of X.X.X.88. A backup system has been set up with two NICs, one on eth0 with IP X.X.X.88, and eth1 with X.X.X.89. I always keep NIC1 (eth0) down, and unplugged (unless it is needed), and only NIC2 (eth1) is connected to the network. (An ifconfig from a client that logged into IP X.X.X.88 showed only an interface with the IP X.X.X.89)

However, for some reason, some clients are having an issue that, when they try to SSH or otherwise connect to X.X.X.88 they end up with the backup server (or, at least, a note that the fingerprint has changed), NOT the primary server. The rest of the clients, including myself, are able to SSH to the two different hosts fine.

On a potentially related note, the backup server can ping the primary, but not vice versa, (but the clients can ping both).

Both servers are plugged into the same switch.

I can't explain it (and thus, can't fix it). Any ideas?

---

### Post by slooow on 2010-04-05
You probably need to have a look how you connect to file- resp backup-server. Could be that the translation from hostname to IP address is mistaken (in /etc/hosts). Or has the file-server (X.X.X.88) and eth0 of the backup server the same IP (X.X.X.88) adress? That would not make much sense?

---

### Post by rpgsimmaster on 2010-04-06
There is no hostname translation, the clients are specifically connecting via IP (which is why this is so weird).

Additionally, yes eth0 on both machines have the same IP (so that if the primary goes down, the secondary can come up with the same IP), but eth0 is down and physically unplugged on the backup machine.

I checked with one of the users, and watched as they entered 'ssh -l [username] X.X.X.88'. They ended up on the backup server, so I got them to login and run an 'ifconfig', which returned 'eth1 [...] inet addr: X.X.X.89'. eth0 was down, and there was no mention of X.X.X.88 anywhere in the output

It's obviously a routing problem, I just don't see anything that might cause it in the network hardware, so I'm wondering if there's something about network interface configuration on Linux I don't yet understand.

---

### Post by renkinjutsu on 2010-04-06
hmm one thing to check is if your router is forwarding you to the wrong machines.. or if you've enabled one of your computers as a router, check those settings (port forwarding).

---

### Post by rpgsimmaster on 2010-04-06
This is entirely on a LAN: Clients come in from various places around the office to a patch panel, which are then patched into several (though, at the moment, just one) 10/100 switches, which are, in turn, patched to a central Gigabit switch, which has both file servers on it. As a result I would suspect the routing hardware if *all* the clients were intermittently failing, but only a select few are. 
I also have no reason to think it's a fault on part of the clients.

I haven't tried changing the patching to see if that would affect it, but it still doesn't explain the intermittent IP collision between two servers which claim to have two very distinct IPs

---

### Post by terazen on 2010-04-06
Can you check what mac addresses the different clients see for x.x.x.88?  If 2 machines are on the same ip subnet they connect to each other via mac addresses so maybe that's the culprit?```
ping -c 3 x.x.x.88
arp -v
```

---

### Post by cdenley on 2010-04-06
When you have two interfaces on the same network, they will each handle traffic for the other. I've noticed this before, but it was never a problem for me. I'm not sure how to prevent this.

I have a server with two network cards. One is assigned 192.168.0.2, the other 192.168.0.9. I receive an ARP reply from both cards for one IP.
```

cdenley@ubuntu:~$ arping -c 1 192.168.0.2
WARNING: interface is ignored: Operation not permitted
ARPING 192.168.0.2 from 192.168.0.31 eth0
Unicast reply from 192.168.0.2 [00:18:F3:F0:4B:3F]  0.614ms
Unicast reply from 192.168.0.2 [00:18:F3:F0:4C:9D]  0.645ms
Sent 1 probes (1 broadcast(s))
Received 2 response(s)

```

---

### Post by terazen on 2010-04-06
Maybe try keeping both nics on the backup server plugged in and disable eth0 through the os?  When you want to use the backup server just ssh to eth1 and enable eth0.

---

### Post by rpgsimmaster on 2010-04-06
@terazen:
I did disable eth0 through the OS, that's the problem; I only took the precaution of physically unplugging the NIC, when the problem was still occurring (to no avail).

@cdenley: Interesting, it didn't occur to me that both NICs on the backup might both be responding to an ARP request for the .88 IP, even when the interface itself is down, and the clients without the problem have already cached the MAC info. As per @terazen's question, I'm 99% sure they (the two different servers) have distinct MAC addresses on each NIC though (I'm not in the office atm, so I can't check). 

I'll run an ARP check next time I'm in the office, and report back; I suspect we'll see that both servers respond to an arp request for .88 even with eth0 off on the backup server... so next question: how do I prevent this? :D

---

### Post by rpgsimmaster on 2010-04-06
Haha! Now that I know that ARP is probably causing the problem, I was able to do a little bit more Googling; it turns out linux, by default, treats IPs as belonging to a machine, not a specific NIC on the machine. The fix(es) are here:

[http://serverfault.com/questions/22253/ubuntu-linux-multiple-nics-same-lan-arp-responses-always-go-out-a-single-n](http://serverfault.com/questions/22253/ubuntu-linux-multiple-nics-same-lan-arp-responses-always-go-out-a-single-n)

---

