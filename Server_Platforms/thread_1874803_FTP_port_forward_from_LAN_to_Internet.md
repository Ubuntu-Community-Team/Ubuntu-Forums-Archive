---
title: "FTP port forward from LAN to Internet"
date: 2011-11-03
forum: Server Platforms
---

### Post by abandonedthe_mulletator on 2011-11-03
Hi,

I have a server setup like this:

Internet <--> eth0 <--> Server A <--> eth1 <--> FTP Server + LAN

I need the FTP server to be accessible from the internet.  I am running VSFTP.

Here's my iptables rules:
```

## Reset rules
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -F
sudo iptables -X
echo "Rules Reset"

## Masquerade settings
sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.3.0/24 -m state --state NEW -j ACCEPT
sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
 echo "Masquerade is Set!"

## FTP Rules
iptables -t nat -I PREROUTING -d <Server A> -p tcp -m tcp --dport 21 -j DNAT --to-destination <FTP Server>
iptables -t nat -I PREROUTING -d <Server A> -p tcp -m tcp --dport 20 -j DNAT --to-destination <FTP Server>
iptables -t nat -I PREROUTING -d <Server A> -p tcp -m tcp --dport 12000:13000 -j DNAT --to-destination <FTP Server>

echo "FTP Forwareded"

```

Also VSFTP has these port settings
pasv_min_port=12000
pasv_max_port=13000

The forwarding seems to half work.  I am able to connect but Filezilla give me this message, "Server sent passive reply with unroutable address. Using server address instead."

Any ideas?

---

### Post by abandonedthe_mulletator on 2011-11-03
OK I got it.  It turns out that I needed to add the following lines to my iptables script:
```
sudo modprobe nf_conntrack_ftp 
sudo modprobe nf_nat_ftp 

```

I hope this helps someone.  It took me a long time to figure this out.

---

