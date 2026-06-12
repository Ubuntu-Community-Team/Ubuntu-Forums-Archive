---
title: "IPtables help"
date: 2006-10-31
forum: Server Platforms
---

### Post by mzracer360 on 2006-10-31
I need to know how to work with IPTables.  I need to allow a certain port.  I cant seem to find any how-to's.  Much help is appreciated!

---

### Post by John.Michael.Kane on 2006-10-31
Have a read [http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables](http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables)

---

### Post by mzracer360 on 2006-11-01
Thanks for the link, but it was too confusing for me.  Heres what I got out of it though:

```
# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N TRUSTED

# Allow https
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 443 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 443 -j ACCEPT

# Allow srcds
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 27015 -j ACCEPT

# End message
echo " [End iptables rules setting]"
```

Not sure if you are familiar with it, but 27015 is used with Counter-Strike Source servers to administer the server while ingame.  Even after setting up the IPtables this way, I cannot admin the server.  I do have that port open in my router.

---

### Post by Ronbo on 2006-11-01
I've been playing around with and learning Firehol [http://firehol.sourceforge.net/]("http://firehol.sourceforge.net/") and for the most part it seems pretty straight forward for setting up iptable rules.

---

### Post by harrysales on 2006-11-14
look in christ edition of linux format mag

---

### Post by mzracer360 on 2006-11-21
I am still having a problem with my IPTables.

Heres what I got so far.

I have a Linksys Wireless G Router (not using wireless connection for this setup though), a Netgear Gigabyte Switch and a D-Link Cable Modem.
Here is my router setup:
[img]http://img.photobucket.com/albums/v242/mzracer360/Misc/ports.jpg[/img]

My IPTable is setup like so:
```
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 27015 -j ACCEPT
```

iptables -L -v -n shows this:
```

Chain INPUT (policy ACCEPT 498K packets, 93M bytes)
pkts bytes target prot opt in out source destination 
0 0 ACCEPT tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp spt:27015

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
pkts bytes target prot opt in out source destination 

Chain OUTPUT (policy ACCEPT 482K packets, 59M bytes)
pkts bytes target prot opt in out source destination
```

When i go to admin my server, i get a "unable to connect to server" error.

---

