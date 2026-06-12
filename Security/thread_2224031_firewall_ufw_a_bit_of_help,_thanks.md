---
title: "firewall ufw: a bit of help, thanks"
date: 2014-05-14
forum: Security
---

### Post by mauricebis on 2014-05-14
How can it be that ufw firewall blocks a request 

(log [20585.206323] [UFW BLOCK] IN=wlan0 OUT=ppp0 MAC=00:16:e3:8e:f7:76:38:e7:d8:ec:62:c2:08:00 SRC=10.10.0.2 DST=208.67.222.222 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=60331 DF PROTO=UDP SPT=16259 DPT=53 LEN=40) 

from the SRC=10.10.0.2 when in fact, I have the rules:

Status: active
Logging: on (high)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
Anywhere                   ALLOW IN    10.10.0.2

This is Ubuntu 12.04, the  IP 10.10.0.2 is Android tablet that accesses through wifi hotspot wlan0.
Thanks.

---

### Post by HiImTye on 2014-05-14
> **mauricebis said:**
> DST=208.67.222.222that's not to your machine, is your machine an intermediary? it could be blocked before UFW in iptables as your machine isn't the destination

---

### Post by spynappels on 2014-05-14
Is this on a server you are using as a router/wireless access point?

That log line seems to suggest the packet came in on the wireless NIC and was supposed to go out to the Internet down a ppp(oe?) network connection.

---

### Post by mauricebis on 2014-05-14
> **spynappels said:**
> Is this on a server you are using as a router/wireless access point?

That log line seems to suggest the packet came in on the wireless NIC and was supposed to go out to the Internet down a ppp(oe?) network connection.

Thanks. Yes, right. I found the answer in this page [https://help.ubuntu.com/10.04/serverguide/firewall.html](https://help.ubuntu.com/10.04/serverguide/firewall.html) and adding the following lines to the iptable:
sudo iptables -A FORWARD -s 10.10.0.0/16 -o ppp0 -j ACCEPT
sudo iptables -A FORWARD -d 10.10.0.0/16 -m state --state ESTABLISHED,RELATED -i ppp0 -j ACCEPT

did the job.

Thank you.

---

