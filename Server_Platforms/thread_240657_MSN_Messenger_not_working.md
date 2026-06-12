---
title: "MSN Messenger not working"
date: 2006-08-21
forum: Server Platforms
---

### Post by ashrack on 2006-08-21
This machine-XUBUNTU has 2NICs. One connects to PPPOE ADSL and the other one to a notebook using WinXP. 
So I've been reading this guide in how to enable internet sharing:
[https://help.ubuntu.com/ubuntu/serverguide/C/firewall-configuration.html](https://help.ubuntu.com/ubuntu/serverguide/C/firewall-configuration.html)

And so I pasted this line into the terminal:
```
sudo iptables -t nat -A POSTROUTING -s 192.168.1.0/16 -o ppp0 -j MASQUERADE
```
And the internet started working on the client WinXP notebook! BUt I'm unable to connect to MSN MESSENGER from it!

So then I installed FIRESTARTER and set it up properly and MSN MESSENGER did connect! 
But I dont want FIRESTARTER or any other kind of FW. 
So what else am a missing here?

---

### Post by Ahriman on 2006-08-21
As far as I am aware, all Firestarter is is a gui to iptables anyway. If you have set an iptables rule then you have a firewall running, imo.

Why don't you want firestarter or any firewall?

---

### Post by ashrack on 2006-08-21
Im not keen on using Firestarter because it has its own problems. Like writing its logs to /var/log/messages and polluting the DMESG output...
And it doesnt work together with DNSMASQ...

---

### Post by ashrack on 2006-08-26
No one knows whay on the client computer MSN wont function when I put this line into the server machine:
```
sudo iptables -t nat -A POSTROUTING -s 192.168.1.0/16 -o ppp0 -j MASQUERADE
```

---

