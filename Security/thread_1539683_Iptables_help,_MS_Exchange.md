---
title: "Iptables help, MS Exchange"
date: 2010-07-26
forum: Security
---

### Post by McDoodleson on 2010-07-26
Hello, I am new to this whole Linux things and iptables are doing my head in.

So far my iptable rules are working to allow me to do the things I need, but when it comes to sending external emails I'm not getting anywhere.

Here is the basic run down of whats happening. I have a LAN (10.0.6.x) consisting of a MS server 2003 DC acting as my primary DNS and external webserver. I also have another MS Server 2003 running my print server, secondary DNS, internal webserver and MS Exchange server. I also have a MS XP workstation and a Asterix Trixbox. Finally I have my Ubuntu Desktop that has two NICs and acts as my firewall/default gateway. The 'Green' side Eth0 is configured to have an IP address in my 10.0.6.x network and the 'red' side eth1 is configured with an IP address in my 172.25.104.x network. The proxy server that my green network gets its internet from is located in the red network. 

As I said all my services so far work. The internet, FTP, HTTP, HTTPs and VPN traffic are all being allowed through. I can send internal emails but I can not send an receive emails externally through the firewall and in and out of the red network.

The rules I have currently are:

sudo iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT
sudo iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT

sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 

sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 8081 -j ACCEPT
sudo iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT
sudo iptables -A OUTPUT -p tcp --dport 8081 -j ACCEPT

sudo iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT
sudo iptables -A INPUT  -p icmp --icmp-type echo-reply   -j ACCEPT
sudo iptables -A INPUT -s 10.0.6.2/24 -j ACCEPT
sudo iptables -A OUTPUT -s 10.0.6.2/24 -j ACCEPT   

sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to-destination 10.0.6.3
sudo iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j DNAT --to-destination 10.0.6.3
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to-destination 10.0.6.0
sudo iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j DNAT --to-destination 10.0.6.0
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 443 -j DNAT --to-destination 10.0.6.3
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 21 -j DNAT --to-destination 10.0.6.3
sudo iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 1723 -j DNAT --to-destination 10.0.6.3

sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 25 -j DNAT --to-destination 10.0.6.0
sudo iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 110 -j DNAT --to-destination 10.0.6.0


I apologise if my explanation is a little all over the place, I am very very new to this and also extremely confused by it all. If anyone has any suggestions that would be muchly appreciated. Thanks :)

---

