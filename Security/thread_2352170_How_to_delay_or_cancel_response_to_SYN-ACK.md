---
title: "How to delay or cancel response to SYN-ACK"
date: 2017-02-10
forum: Security
---

### Post by courtney2 on 2017-02-10
I apologize if this is a bad subforum for this topic, but I saw Snort as a sticky topic so I assume this is the right place. I'm working on setting up a NIDS box using Bro, and I am experimenting with creating a theoretical baseline of network traffic. Part of that is TCP connections to my web server, and I'm wanting to get Bro to send alerts on an abnormal amount of SYN packets with no response to the SYN-ACK. Because of that, my "attacker" machine will either need to block incoming SYN ACK packets at the firewall, or what I would prefer is I want to write a script that will send a SYN packet, get the SYN ACK, but won't send an ACK. How can I do this? I want to leave a disclaimer that this is entirely for educational purposes, will be done only on an internal virtual network, and is part of a class assignment. My reasoning for doing this is in the real world a server will wait for an ACK and sometimes may not get the ACK and therefore drop the session made with that client and I want to simulate that

---

### Post by TheFu on 2017-02-11
Real-world, we block this stuff.
[https://www.cyberciti.biz/tips/linux-iptables-10-how-to-block-common-attack.html](https://www.cyberciti.biz/tips/linux-iptables-10-how-to-block-common-attack.html) might be helpful.
[https://www.cyberciti.biz/tips/linux-iptables-examples.html](https://www.cyberciti.biz/tips/linux-iptables-examples.html) is another set.

---

### Post by The Cog on 2017-02-11
This command will make your laptop able to only send SYN packets to the victim (192.168.0.103 in this case)
```
sudo iptables -A OUTPUT -p tcp -d 192.168.0.103 --tcp-flags SYN NONE -j REJECT
```
Then every time you run this command it will send another SYN and nothing else. The REJECT makes nc exit quickly, so you can run it repeatedly and tie up server resources:
```
nc 192.168.0.103 22
```

---

### Post by courtney2 on 2017-02-16
Real world the stuff gets blocked, but in the studies world we learn to use and create the stuff that lets organizations block it. Thank you for the information, I didn't want to play with iptables atm, the problem with the Cyberciti links is they talked about blocking  those at the firewall level, when I'm trying to instigate the attack and  I wanted the server to respond. I found that hping3 actually has an option for sending SYN packets, and at increments of time too. But for future testing I'm going to try out your option TheFu and The Cog. Thank you!

---

