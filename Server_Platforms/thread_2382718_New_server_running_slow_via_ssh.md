---
title: "New server running slow via ssh"
date: 2018-01-16
forum: Server Platforms
---

### Post by sniper8752 on 2018-01-16
I am running 16.04, and it seems to be running slow via ssh (lag time between hitting a key, and the key showing up/the terminal responding to input). It also takes longer now to establish the ssh connection from the lan.  What are some ways to best diagnose the issue, and what is going on?
What it's running: dnsmasq, ssh, and openvpn.  I am using iptables for the firewall.
When logging in via ssh, here are some stats:

System load:  0.0                Users logged in:     1
  Usage of /:   0.2% of 900.84GB  
  Memory usage: 1%                
  Swap usage:   0%                 
  Processes:    123

I just want to make sure there is nothing especially malicious going on here...

I can also post iptable rules, if need be.

Attached image: Running wireshark while connecting via ssh, I got a good amount of these packets, which I'm guessing, is not healthy.  Also have a few TCP spurious retransmission packets.

---

### Post by TheFu on 2018-01-16
ssh -vvvv
Check the server-side logs.

---

