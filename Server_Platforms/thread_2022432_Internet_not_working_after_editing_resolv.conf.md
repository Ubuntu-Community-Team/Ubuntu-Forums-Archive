---
title: "Internet not working after editing resolv.conf"
date: 2012-07-10
forum: Server Platforms
---

### Post by regnumimbriumx on 2012-07-10
Hi All,
 
Advance apologies for noob inquiry; I haven't done server maintenance in a few years and recently did a full install of 12.04 server. I've now spent ~40 hours trying to fix one particular problem and need the experts!
 
I own a domain name, [www.example.com]("http://www.example.com"). I did a server install that did not follow, but pretty much mirrored this guide ([http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3-p3](http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3-p3)). I wanted a static ip address for the server on my home network so I updated /etc/resolv.conf to include my nameservers (this is apparently a futile gesture, as resolv.conf gets overwritten every reboot) and restarted the network. This broke my ability to access internet from the server. I could still navigate to the server from computers on totally different networks but the server itself can't ping any external networks/servers. 
 
Following the guide in the previous link, I went through, from step 7, updating everything I could think of. My current /etc/network/interfaces:
 
```
 
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.254
        netmask 255.255.255.0
        network 192.168.1.100
        broadcast 192.168.1.255
        gateway 192.168.1.1
        dns-nameservers ns1.aplus.net ns2.alpus.net ns3.aplus.net

```
 
Then I did "/etc/init.d/networking restart".
 
Edited /etc/hosts to:
```
 
127.0.0.1       localhost.localdomain   localhost
192.168.1.254   [www.example.com]("http://www.example.com")     userv
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```
 
Then ran following commands:
"echo [www.example.com]("http://www.example.com") > /etc/hostname"
"/etc/init.d/hostname restart"
"hostname"
"hostname -f"
 
The last two commands both showed [www.example.com]("http://www.example.com")
During my attempts to fix this, I also changed /etc/dhcp/dhclient.conf (per [http://askubuntu.com/questions/140688/upgraded-server-to-12-04-dns-no-longer-working](http://askubuntu.com/questions/140688/upgraded-server-to-12-04-dns-no-longer-working)), adding:
prepend domain-name-servers ns1.aplus.net, ns2.aplus.net, ns3.aplus.net;
That didn't help, but I left the changes in the file. Then I tried renaming resolv.conf to backup.resolv.conf (per this post: [http://askubuntu.com/questions/142327/can-not-access-internet-dns-names-do-not-resolve-after-update-today](http://askubuntu.com/questions/142327/can-not-access-internet-dns-names-do-not-resolve-after-update-today)), which didn't help either. After restarting the system, internet doesn't work and I cannot even reach the server from external websites anymore. It appears that backup.resolv.conf was deleted and replaced with a much larger, more complicated file. Unfortunately, my server is halfway across the country and I've only got some atechnical people who can do hands-on work on it, at this point. 
 
To recap: I was able to access my server via putty, ftp software, and any internet-enabled browser; my server, however, still could not access the internet for commands like "apt-get update" or anything else at all. After renaming resolv.conf, I can do neither. It sounded like I was having the same problem that this person did, except that I couldn't follow how I was actually supposed to fix it: [http://serverfault.com/questions/390986/ubuntu-server-12-04-can-access-lan-but-not-internet](http://serverfault.com/questions/390986/ubuntu-server-12-04-can-access-lan-but-not-internet)
 
Any thoughts on what I'm missing? A basic understanding of linux? :) If there's any way to salvage this mess, I'd be hugely grateful. 
 
Thanks so much for any help offered!!!
 
Possibly relevant details:
my domain: [www.example.com]("http://www.example.com")
my host: aplus.net (purported nameservers: ns1.aplus.net, ns2.aplus.net, ns3.aplus.net)
my internet connection details, provided by router:
Connection Type: Automatic Configuration - DHCP
Internet IP Address: XXX.14.243.XXX
Subnet Mask: 255.255.240.0
Default Gateway: 24.14.240.1
DNS1: 75.75.75.75
DNS2: 75.75.76.76
my network setup, assigned in router:
ip address: 192.168.1.1
subnet mask: 255.255.255.0
start ip address: 192.168.1.100

---

### Post by papibe on 2012-07-10
Hi regnumimbriumx. Welcome to the forums!

First, you have to play the rules of your own network (LAN). Make sure that your static IP (192.168.1.254) is outside your DHCP range.

If I understood correctly this information:
> start ip address: 192.168.1.100
It is not. Choose an address lower than 100.

Then, I think you made a typo on your interfaces:
```
network 192.168.1.100
```
My guess the correct line should be:
```
network 192.168.1.0
```
I hope that helps, and tell us how it goes.
Regards.

---

### Post by Cheesemill on 2012-07-11
> **regnumimbriumx said:**
> 
```
 
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.254
        netmask 255.255.255.0
        network 192.168.1.100
        broadcast 192.168.1.255
        gateway 192.168.1.1
        dns-nameservers ns1.aplus.net ns2.alpus.net ns3.aplus.net

```

dns-nameservers needs to be in a format your computer can resolve, ie IP addresses (or a host that's in your hosts file).

How is your server meant to work out the IP addresses of your nameservers if it can't work out the IP addresses of the nameservers?

---

### Post by SeijiSensei on 2012-07-11
> **Cheesemill said:**
> dns-nameservers needs to be in a format your computer can resolve, ie IP addresses (or a host that's in your hosts file).

Or, perhaps more directly, use the DNS servers IP addresses in dns-nameservers, not their hostnames.

---

### Post by Chaosadnd on 2012-07-11
Hi there, 

I was going to point out the typo for network, but that was already pointed out. But your name servers need to point to dns, not hostnames. Be it comcast nameservers, or your own personal nameservers. I tend to put in both. But remove the hostnames, and put the IP addresses, and all should be fine.

---

