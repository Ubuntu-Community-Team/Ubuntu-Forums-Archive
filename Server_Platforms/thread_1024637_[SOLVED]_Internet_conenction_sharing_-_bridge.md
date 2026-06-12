---
title: "[SOLVED] Internet conenction sharing - bridge"
date: 2008-12-29
forum: Server Platforms
---

### Post by confuded92 on 2008-12-29
Hello,

I have a Ubuntu Server 8.04 instaled on a box with two network cards. eth0 is the one recieving a static ip and eth1 is ment to connect to a hub/switch, which is connected to several Windows XP machines.

I want to have a "bridge" from eth0 to eth1, so that the several machines connected to the hub will have internet and the actuall Ubuntu Server machine should also have internet with a real/static IP address (since there is a web and email servers there; plus a domain name is asigned to that IP).

I have tried a couple of tutorials, but I ended up loosing the internet connection on the server machine (does not ping google.com).

Thanks!



P.S. Here is my "/etc/network/interfaces"

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 83.241.17.62
        netmask 255.255.255.0
        network 83.241.17.0
        broadcast 83.241.17.255
        gateway 83.241.17.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 83.241.1.2 83.241.16.2
        dns-search 913.lv

auto eth1
iface eth1 inet static
        address 10.0.0.1
        netmask 255.255.255.0
```

---

### Post by alenis on 2008-12-29
To share the internet connection you should enable NAT, which can be done through iptables. For example, my server has network adapters configured as follows:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.1
netmask 255.255.255.0

auto eth1
iface eth1 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

```
eth1 is connected to a modem/router, eth0 to the LAN switch.
A safe way to enable NAT should be (I am a beginner with IP tables and maybe safety could be improved) the following:
```

iptables -P FORWARD DROP
iptables -A FORWARD -i eth1 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

```
You also have to open ports and enable network traffic for your server.

---

### Post by iponeverything on 2008-12-29
also add this to your rc.local to forward the packets. run the echo command
with sudo from the command line to have it take effect without having to reboot.
 
```

echo 1 > /proc/sys/net/ipv4/conf/all/forwarding
exit 0

```

---

### Post by confuded92 on 2008-12-29
alenis, thanks for the suggestion. But you have mentioned about opening ports on the server after these commands right? Which means I cannot execute the above via SSH?
Or can I enable ssh and other ports first and then set up the NAT?

I do have physical access, it's just annoying to rewire the keyboard and screen... :( (I know I can get some sort of a switch, whatever they are called, but this is a a server right?).

Thank you for all your replies. I will try to execute the above (respectively to my configuration) as soon as I receive a reply bout opening ports. :) I can't just leave the web server down for more than 5 minutes (or my boss scream from his room "why is the web down!??!" :)"

~confuded

---

### Post by iponeverything on 2008-12-29
If the services are running on the same machine that is doing the masquerading, in the case of the above rules - you will not need to make any modifications to allow access to them.

The FORWARD table only affects traffic passing through the machine and not traffic *for* the box.

You would be smart to consider every service running on the box, determine the ip address ranges that are going to need access to those services and and restrict them accordingly. Don't run unnecessary services and set up a basic log monitor to email you when strange things pop up in the logs.

---

### Post by alenis on 2008-12-30
As far as I understand how iptables works, if you choose an ACCEPT policy for the filter table, i.e.
```

iptable -P INPUT ACCEPT
iptable -P OUTPUT ACCEPT

```
you don't have to issue other iptables commands to have your servers working. However, ACCEPTing everything is dangerous, so you may prefer a DROP policy and then specific commands to accept only the traffic you want.
I have a working configuration at work. I cannot check it now, but the following commands should allow the services your are interested in:
```

iptable -P INPUT DROP
iptable -P OUTPUT DROP

# enable loopback
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

# enable SSH
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 22 -j ACCEPT

#enable HTTP
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 80 -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 443 -j ACCEPT

# this is needed if you want to surf the web from the server

iptables -A OUTPUT -j ACCEPT -m state \
  --state NEW,ESTABLISHED,RELATED -o eth0 -p tcp \
  -m multiport --dports 80,443 --sport 1024:65535

iptables -A INPUT -j ACCEPT -m state --state ESTABLISHED,RELATED  \
-i eth0 -p tcp

# these should enable your http server
iptables -A INPUT -j ACCEPT -p tcp -i eth0 -m multiport --sports 1024:65535 -m state --state NEW,ESTABLISHED,RELATED 

iptables -A OUTPUT -j ACCEPT -p tcp -o eth0 -m multiport --dports  80,443,1024:65535 -m state --state ESTABLISHED,RELATED 

```

These commands should work. Those relating to HTTP traffic are a bit intricate and not very elegant but should be safe. However, I would like to have advice from some iptables expert about a safe and simple configuration for HTTP/HTTPS traffic.

---

### Post by confuded92 on 2009-01-01
Wow! Thank you very much! These are probably one of the most helpfull and informative replies I have ever recieved! :o

I shall try the setup today at work :). Thanks again!

~confuded

EDIT:

The internet works on the windows machine (using crossover). I had to manually asign all the values: IP, netmask, gateway and the DNS server as in the server /etc/network/interfaces.

Is there a way for all these values to be assigned automatically? Like a DHCP  server which also assigns the DNS servers?

---

### Post by iponeverything on 2009-01-03
It pretty easy to setup a dhcp server which can also hand out nameserver addresses.

```

sudo apt-get install dhcp3-common
sudo apt-get install dhcp3-server

```

config file is /etc/dhcp3/dhcpd.conf

do a:

```
man dhcpd.conf
```

for the format of the file.. it fairly easy. Google around for "dhcp3 dhcpd.conf" and you will find a number examples.

---

### Post by confuded92 on 2009-01-04
Thanks, I've figured that out using Google :).

Though I have a problem with the default gateway... :( I'll solve it! 

Thanks to all!

~confuded

---

