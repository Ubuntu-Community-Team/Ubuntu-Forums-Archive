---
title: "need to set up port fowardingin"
date: 2008-08-19
forum: Security
---

### Post by killerasp on 2008-08-19
i am running 8.04 server on my machine with vmware server with some vm's running on private interface 192.168.1.X/24. I currently use UFW to filter ports and such. So far from what i see, ufw is not capable of port fowarding. my server is using a static ip on its eth0. i want to be able to forward ports on my host machine to the VMs. can anyone suggest a way for me to do accomplish this? 

thanks ahead of time.

---

### Post by jerome1232 on 2008-08-19
ufw is a frontend to iptables, iptables itself is capable of port forwarding

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by HermanAB on 2008-08-19
# Forward SQL Ledger Apache port 8000/tcp to the Mdv2008 Virtual machine for testing
# Port 8000/tcp is also opened in the Firewall wizard
iptables -t nat -I PREROUTING -i eth0 -p tcp --dport 8000 -j DNAT --to-destination 192.168.1.14
iptables -I FORWARD -p tcp -m state --state NEW -d 192.168.1.14 --dport 8000 -j ACCEPT

Cheers,

Herman

---

