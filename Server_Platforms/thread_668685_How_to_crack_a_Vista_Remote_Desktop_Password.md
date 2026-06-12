---
title: "How to crack a Vista Remote Desktop Password"
date: 2008-01-15
forum: Server Platforms
---

### Post by xluryan on 2008-01-15
Ok, I do a lot of security auditing and have been really curious lately as to how to do this from Linux. I know with Winblows you can download "Cain and Abel", which has a built in ARP poisioner/Remote Desktop Password sniffer, but I don't use Winblows.

How would one accomplish this strictly with Linux?

(Educational purposes only)

---

### Post by alex_0077 on 2008-01-15
Would WINE (WINE Is Not an Emulator) work? :popcorn:

---

### Post by aboutblank on 2008-01-15
Ettercap

WARNING: Do not be stupid!

---

### Post by HermanAB on 2008-01-16
In general, Windows security relies a lot on the clients being well behaved.  Which of course explains why it is relatively easy to hack, since all you need to do is write a misbehaving client.

Windows XP, by default allows remote desktop clients to log in by sending the username and password in plain text.  However, I am not aware of any mainstream client programs that do that.  All the Linux remote desktop clients will encrypt the user name and password.

Soooo, if you can find a client program (or hack a Linux one) that doesn't encrypt the username and password, then you can easily sniff it with tcpdump and grep.

There is a security policy that can be set to enforce encryption, but as I said, it is off by default.

Cheers,

Herman

---

### Post by xluryan on 2008-01-16
To Herman:
Ok, I see. But it's more like this: I have three computers in my apartment. 1 is running Vista, 2 has XP, and 3 is Ubuntu. I would like 2 to connect to 1, while 3 is watching that connection and grabs the password. How would I do that?

To aboutblank:
Ettercap does not seem to have a built-in plugin for Remote Desktop. Any advice as to how I'd implement it for that? Because it seems like an AMAZING tool otherwise and I'll surely enjoy delving into it over these next few days.

---

### Post by HermanAB on 2008-01-16
For a three party affair, you need to use a network hub, not a switch.  A hub will send all data packets to all ports.  A switch only sends packets to the two linked ports, so other ports cannot see the data.  Another option is to run tcpdump or wireshark on one of the two PCs involved.

---

### Post by Rizado on 2008-01-16
> **HermanAB said:**
> For a three party affair, you need to use a network hub, not a switch.  A hub will send all data packets to all ports.  A switch only sends packets to the two linked ports, so other ports cannot see the data.  Another option is to run tcpdump or wireshark on one of the two PCs involved.You can easily  mac flood most cheap switches. They will then start to behave like a hub, broadcasting all packets to everyone.

A more subtle approach would be arp spoofing. You simply trick the router that you are the client and the other way around. 

MAC flooding will make the switch run out of memory in which it keeps track on what goes where and to not stop connection completely it will send everything everywhere unless configured not to. Nice method of gathering data from lots of computers but is not so "stealthy" maybe. And remember your data will be available for everyone else as well. Arp spoofing is more subtle and more effective agains a single victim.

You could probably do this with ettercap although I haven't tried it. I have tried arpspoof from the dsniff package together with some sniffers from the same package and wireshark with good resault :)
MAC flooding can be done by using macof also from the dsniff package, although I havn't tried it either.

---

