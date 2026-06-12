---
title: "IPtables as my second firewall."
date: 2008-03-12
forum: Security Discussions
---

### Post by EMCGFX on 2008-03-12
I will use the iptables as my second firewall, my router bing the first. Here is the rule set from my firewall, did I due it right and how can I improve it =D

```
#!/bin/bash

### Help ###
# DENY; makes it seems as if no connection exists.
# REJECT; simply refuses the connection.

# Flush all chains
iptables -F

# Block all by default
# iptables -P INPUT DROP
# iptables -P OUTPUT DROP
# iptables -P FORWARD DROP

# Create custom rule chains
# iptables -N bad_packets
# iptables -N bad_tcp_packets
# iptables -N icmp_packets
# iptables -N udp_inbound
# iptables -N udp_outbound
# iptables -N tcp_inbound
# iptables -N tcp_outbound

# Populate user chains
# iptables -A bad_packets -p ALL -m state --state INVALID -j LOG \
#    --log-prefix "Invalid packet: "
# iptables -A bad_packets -p ALL -m state --state INVALID -j DROP
# Then check the tcp packets for additional problems
# iptables -A bad_packets -p tcp -j bad_tcp_packets
# All good, so return
# iptables -A bad_packets -p ALL -j RETURN

# Allow Established Sessions
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow Incoming Traffic on Specific Ports
# iptables -A INPUT -p tcp --dport ssh -j ACCEPT
# Allow All Incoming Web Traffic
# iptables -A INPUT -p tcp --dport 80 -j ACCEPT
# Allow DHCP for dynamic ips
# iptables -A INPUT -j ACCEPT -i eth0 --source 0/0 -p udp --sport 67 --dport 68

# Allow localhost loopback port
iptables -I INPUT 1 -i lo -j ACCEPT

# Allow internal network
iptables -A INPUT -s 192.168.0.0/16 -d 192.168.0.0/16 -j ACCEPT
iptables -A FORWARD -s 192.168.0.0/16 -d 192.168.0.0/16 -j ACCEPT


######################
### Blocking Rules ###
######################

# Block local open ports
# iptables -A INPUT -p tcp -s 0/0 -d 0/0 rpcbind -j DENY  # port 111
# iptables -A INPUT -p tcp -s 0/0 -d 0/0 netbios-ssn -j DENY  # port 139
# iptables -A INPUT -p tcp -s 0/0 -d 0/0 microsoft-ds -j DENY  #port 445
# iptables -A INPUT -p tcp -s 0/0 -d 0/0 ipp  # port 631
# iptables -A INPUT -p tcp -s 0/0 -d 0/0 nfs  # port 2049

# Blcok all udp connections on well-known ports.
iptales -A INPUT -p udp -s 0/0 -d 0/0 0:1023 -j DENY

# Block ping of death attack
iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -j ACCEPT

# Block new incoming requests *TEST*
iptables -A INPUT -i eth0 -m state --state NEW,INVALID -j DROP
iptables -A FORWARD -i eth0 -m state --state NEW,INVALID -j DROP

# Blocking All Incoming Traffic
iptables -A INPUT -j DROP
iptables -A FORWARD -j DROP

# Blocking All Outgoing Traffic
# iptables -A OUT

# Loggin
# iptables -I INPUT 5 -m limit --limit 5/min -j LOG --log-prefix "iptables denied: "

iptables-save

# Restore IPTables: iptables-restore

# Configuration on Startup
# sudo sh -c "iptables-save > /etc/iptables.rules"


# Block specific ip
# This rule blocks any incoming traffic from 10.20.30.40
# iptables -A INPUT -s 10.20.30.40 -j DROP
# This rule blocks any incoming traffic for LAN computer 10.20.30.40
# iptables -A INPUT -d 10.20.30.40 -j REJECT

# Allow specific ip
# This rule accepts incoming traffic from source ip to destination ip wich is a ftp server.
# iptables -A INPUT -s 10.20.30.40 -d 40.30.20.10 -p tcp --dport 21
```

NOTE: A lot of it disable for now. Any iptables guru are welcome to help.

---

### Post by konungursvia on 2008-03-12
With your router, and with the IPtable default settings, you should be fine. All linux ports are closed by default, so you hardly need any firewall protection anyhow.

---

### Post by EMCGFX on 2008-03-12
> **konungursvia said:**
> With your router, and with the IPtable default settings, you should be fine. All linux ports are closed by default, so you hardly need any firewall protection anyhow.

What do you mean? How can the ports be closed by default if my firewall was empty.

---

### Post by p_quarles on 2008-03-13
> **EMCGFX said:**
> What do you mean? How can the ports be closed by default if my firewall was empty.
Because a port is only "open" if a service is listening for connections on that port. If you aren't running any server software, the system isn't going to acknowledge any external requests. Using "nmap" is a good way to see if anything on your system is actually open. E.g.,:
```
nmap -P0 *your-ip-address*
```
If you're not sure how to do this, here's an easy two step way of getting this done:
1. ```
sudo apt-get install curl nmap
```
2. ```
nmap -P0 $(curl www.whatismyip.org)
```
After running the first step, you can run the second part at any time you have any concerns. It will return a list of any "interesting" ports that can be seen from outside. Once you have this knowledge, you're in a better position to make decisions about further locking down your system.

---

### Post by EMCGFX on 2008-03-13
@ p_quarles, I know how to use nmap :) What I need is help with my iptables rules ;-)) If you know any improvements post.

---

### Post by p_quarles on 2008-03-13
> **EMCGFX said:**
> @ p_quarles, I know how to use nmap :) What I need is help with my iptables rules ;-)) If you know any improvements post.
Improvements would depend entirely on what you're trying to do. My point is that if you're just trying to lock down your system, you don't need to do anything. My suggestion to scan for open ports was based on your last question, which indicated you were under the impression that ports which aren't blocked by packet filtering rules are somehow insecure.

---

### Post by Nerdriot on 2008-03-13
I'm still a noob, so I'm really enjoying this conversation, as it's teaching me ;)

I ran nmap -P0 127.0.0.1, and it gave me 2 open ports, that I'm not sure about at all.

I know one is "privoxy" ( 8118 ), but the other, I dunno. Says "ipp", (port 631). Anyone know what that could be?

---

### Post by EMCGFX on 2008-03-13
@ Nerdriot, hehe I am glad its helping some one.

My ports are all filtered =D

---

### Post by handydan918 on 2008-03-13
> **Nerdriot said:**
> I'm still a noob, so I'm really enjoying this conversation, as it's teaching me ;)

I ran nmap -P0 127.0.0.1, and it gave me 2 open ports, that I'm not sure about at all.

I know one is "privoxy" ( 8118 ), but the other, I dunno. Says "ipp", (port 631). Anyone know what that could be?

Port 631 is ipp (internet printing protocol). Best to leave that alone if you have a printer hooked up.

:)

---

### Post by EMCGFX on 2008-03-14
OK, this is wild. How come each time I start my Ubuntu it clears my iptable rules, even do I save it. *look in the script*. I use iptables-save, is there any where else I need to save this ?

---

### Post by p_quarles on 2008-03-14
> **EMCGFX said:**
> OK, this is wild. How come each time I start my Ubuntu it clears my iptable rules, even do I save it. *look in the script*. I use iptables-save, is there any where else I need to save this ?
The simple iptables-save command doesn't actually save anything to a permanent file, so it won't be there when you reboot. 

Once you have your rules set up the way you want them, you can save them to a file:
```
sudo sh -c "iptables-save > /etc/iptables.up.rules"
```
To load these rules on startup, you will need to tell the system to do so by editing /etc/network/interfaces. Add the following directly underneath the line(s) for your main interface:
```
pre-up iptables-restore < /etc/iptables.up.rules
```

---

### Post by EMCGFX on 2008-03-14
Haha, I kind of figure that out ;-) I knew its not saving it properly, but was not sure how to due this. Thank You, p_quarles ;-) Really nice tip. Whoohoo!

---

### Post by EMCGFX on 2008-03-14
@ p_quarles, OK, I've tried this and my ubuntu stoped working ;-) Its good that I know how to use shell + vi. LOL Steel after fixing it my ubuntu started loading slightly slower. Oh, well I guess I will use my hardware firewall for now and soon AlphaShield ;-)) hehe

---

### Post by p_quarles on 2008-03-14
Hmm. That's certainly strange. I didn't notice anything in your rules that would cause the system to stop working altogether, but maybe I just missed it.

There are, of course, many rule-building front-ends, and scripts. I recall even seeing a web site once where you checked off a few boxes depending on what you wanted to do, and it fed you back a script that would implement the rules you would want. 

Assuming that your /etc/iptables.up.rules file is sufficiently different from the script you posted earlier, you could post that here for others to look over.

---

### Post by EMCGFX on 2008-03-14
The only thing I did diferent then you showed here is instead of /etc/iptables.up.rules I've saved it to /etc/iptables.rules (without 'up' word). But I don't think that could be a problem. Unless there was iptables.rules default file LOL

Also, I have this anoying bug now, I can't scroll up with my mouse third button =( You know where to fix that ? I tried the mouse, but its not there. The scroll down is working, but when I scroll up I get left button menu for some strange reason.

---

### Post by EMCGFX on 2008-03-15
Never mind about mouse ;-) I fixed it. Acasanly I use KVM box for my second pc, by unpluging the mouse from KVM box and connecting it directly to my pc it works just like before again. All I will need to due later is shut down my KVM box by unpluging everything from it and the pluging everything back. It will fix the error, it happes some times.

---

### Post by tad1073 on 2008-03-15
If I want to block a block of addresses can I use 0.0.0.0/255?

Will that block addresses 0.0.0.0, 0.0.0.1, 0.0.0.2 to 0.0.0.255?

---

### Post by EMCGFX on 2008-03-15
Read this should help: [http://www.linuxquestions.org/questions/linux-security-4/block-whole-ip-range-with-iptables-469432/](http://www.linuxquestions.org/questions/linux-security-4/block-whole-ip-range-with-iptables-469432/)

---

