---
title: "security"
date: 2013-01-14
forum: Security
---

### Post by Toriku on 2013-01-14
I was examining all of todays failed ssh login attempts and blocked IP addresses in the log files associated with security this morning, and I can't help but wonder:

   a) what more I can do to beef up security further
         ~ I've got the firewall set up, and DenyHosts
   b) how I can tell if someone has compromised my system
         ~ no damage yet, but there are an awful lot of CRON jobs in the log running root despite there not being any displayed in CronTab

---

### Post by howefield on 2013-01-14
Thread moved to the "*Security Discussions*" forum.

You'll find some great information in the stickies in this forum.

---

### Post by Toriku on 2013-01-14
> **howefield said:**
> Thread moved to the "*Security Discussions*" forum.

You'll find some great information in the stickies in this forum.

thanks, I was just reading through some of those

---

### Post by samiux on 2013-01-14
> **Toriku said:**
> I was examining all of todays failed ssh login attempts and blocked IP addresses in the log files associated with security this morning, and I can't help but wonder:

   a) what more I can do to beef up security further
         ~ I've got the firewall set up, and DenyHosts
   b) how I can tell if someone has compromised my system
         ~ no damage yet, but there are an awful lot of CRON jobs in the log running root despite there not being any displayed in CronTab

Please note that the system logs are for reference only and it cannot indicate that your system is compromised or not but it may show you that someone else want to break into your system.  You can read [this]("http://ubuntuforums.org/showthread.php?t=2098945") for more information.  Please also note that the information provided as above is for reference only.  It is not a bible.

Samiux

---

### Post by movieman on 2013-01-15
> **Toriku said:**
> what more I can do to beef up security further

Put SSH on a port other than 22 and script kiddies will ignore you in future. The only crackers likely to run full port-scans for SSH are the ones who know you have something they want.

---

### Post by haqking on 2013-01-15
> **movieman said:**
> Put SSH on a port other than 22 and script kiddies will ignore you in future. The only crackers likely to run full port-scans for SSH are the ones who know you have something they want.

it is fairy trivial to type

```
nmap -sV <ip>
```

;-)

---

### Post by Ms. Daisy on 2013-01-15
> **haqking said:**
> it is fairy trivial to type

```
nmap -sV <ip>
```

;-)Ha ha with that scan port 4444 is totally secure and safe!

---

### Post by SeijiSensei on 2013-01-15
> **haqking said:**
> it is fairy trivial to type

```
nmap -sV <ip>
```

True, but many SSH attempts are simply automated processes.  There isn't a human at the other end, just a machine trying to identify possible targets.  

OP, unless you expect to be connecting to the server from unknown locations, the simplest solution is to enable connections from specific trusted IPs with iptables and block the rest.

```
iptables -A INPUT -p tcp -s 10.10.10.10 --dport 22 -j ACCEPT
iptables -A INPUT -p tcp -s 10.10.10.11 --dport 22 -j ACCEPT
[etc.]
iptables - A INPUT -p tcp --dport 22 -j REJECT

```

I handle connections from unknown locations by running an OpenVPN tunnel between my laptop and my server.  That opens just a single UDP port for the encrypted traffic.  I use a simple [shared static-key]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") configuration.  Even if someone finds the open port, without the key there isn't any way to exploit it.

---

### Post by CharlesA on 2013-01-15
> **SeijiSensei said:**
> True, but many SSH attempts are simply automated processes.  There isn't a human at the other end, just a machine trying to identify possible targets.  

OP, unless you expect to be connecting to the server from unknown locations, the simplest solution is to enable connections from specific trusted IPs with iptables and block the rest.

```
iptables -A INPUT -p tcp -s 10.10.10.10 --dport 22 -j ACCEPT
iptables -A INPUT -p tcp -s 10.10.10.11 --dport 22 -j ACCEPT
[etc.]
iptables - A INPUT -p tcp --dport 22 -j REJECT

```

+1. That is how I have mine set up.

---

### Post by haqking on 2013-01-15
> **SeijiSensei said:**
> True, but many SSH attempts are simply automated processes.  There isn't a human at the other end, just a machine trying to identify possible targets.  

OP, unless you expect to be connecting to the server from unknown locations, the simplest solution is to enable connections from specific trusted IPs with iptables and block the rest.

```
iptables -A INPUT -p tcp -s 10.10.10.10 --dport 22 -j ACCEPT
iptables -A INPUT -p tcp -s 10.10.10.11 --dport 22 -j ACCEPT
[etc.]
iptables - A INPUT -p tcp --dport 22 -j REJECT

```

I agree, i always recommend changing the default port, use fail2ban, keys, IPTables etc etc

It was just a <sarcasm> response to usual nonchalance of "change the port" which makes it sound secure.

banner grabbing is your friend here ;-)

---

### Post by CharlesA on 2013-01-15
> **haqking said:**
> banner grabbing is your friend here ;-)

Mmmm nc. ;)

---

### Post by movieman on 2013-01-16
> **haqking said:**
> It was just a <sarcasm> response to usual nonchalance of "change the port" which makes it sound secure.

Maybe you could have tried reading my whole post, where I was quite clear that it wouldn't stop people who really want to break into your system.

But script kiddies just try a few well-known ports and then move on to the next IP address, they don't waste time port-scanning the entire range. Nor do they sit at their computer manually typing commands, that's why they're called 'script kiddies'.

The single best way to protect against SSH attacks is to use a non-standard port. Then you can worry about the other 1% who will actually do a port scan.

Oh yeah, and if you try nmap on my firewall you'll be blocked after checking a few ports, unless you do it so slowly that you don't trigger the port-scan detection.

---

### Post by Toriku on 2013-01-18
thanks for all your help guys!

---

