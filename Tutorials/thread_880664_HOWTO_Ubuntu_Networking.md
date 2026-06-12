---
title: "HOWTO Ubuntu Networking"
date: 2008-08-05
forum: Tutorials
---

### Post by ajmorris on 2008-08-05
Here is a networking tutorial with what I think are some handy CLI commands to know.
Feel free to comment and/or make suggestions. Make sure you know what a command does before
issuing it, especially in the security orientated ones.
 
You may also like to see my tutorial on getting to know your ubuntu system better: [http://ubuntuforums.org/showthread.php?t=842307](http://ubuntuforums.org/showthread.php?t=842307) 
 
 
**[SIZE=2][COLOR=red]*Debugging*[/COLOR][/SIZE]**
 
# Show the ethernet status
```
ethtool eth0
```
 
# Force 100Mbit Full duplex
```
ethtool -s eth0 speed 100 duplex full
```
 
# Disable auto negotiation
```
ethtool -s eth0 autoneg off
```
 
# Blink the ethernet led
```
ethtool -p eth0
```
 
# Display all interfaces (similar to ifconfig)
```
ip link show
```
 
# Bring device up (or down). Same as "ifconfig eth0 up"
```
ip link set eth0 up
```
 
# Display all IP addresses (similar to ifconfig)
```
ip addr show
```
 
# Similar to arp -a
```
ip neigh show
```
 
# Ping on ethernet layer
```
arping 192.168.16.254
```
 
# uses tcp instead of icmp to trace throught firewalls (install via sudo apt-get install tcptraceroute)
```
tcptraceroute -f 5 cb.vu
```
 
 
***[SIZE=2][COLOR=red]Routing[/COLOR][/SIZE]***
 
*Print routing table*
 
# use "ip route"
```
route -n
```
 
```
netstat -rn
```
 
 
*Add and delete a route*
 
```
route add -net 192.168.20.0 netmask 255.255.255.0 gw 192.168.16.254
```
 
# same as above with ip route
```
ip route add 192.168.20.0/24 via 192.168.16.254
```
 
```
route add -net 192.168.20.0 netmask 255.255.255.0 dev eth0
```
 
```
route add default gw 192.168.51.254
```
 
# same as above with ip route
```
ip route add default via 192.168.51.254 dev eth0
```
 
```
route delete -net 192.168.20.0 netmask 255.255.255.0
```
 
 
***[COLOR=red]Configure additional IP addresses[/COLOR]***
 
# First IP
```
ifconfig eth0 192.168.50.254 netmask 255.255.255.0
```
 
# Second IP
```
ifconfig eth0:0 192.168.51.254 netmask 255.255.255.0
```
 
# Equivalent Commands:
```
ip addr add 192.168.50.254/24 dev eth0
```
```
ip addr add 192.168.51.254/24 dev eth0 label eth0:1
```
 
 
***[COLOR=red]Change MAC address[/COLOR]***
 
#Normally you have to bring the interface down before the change. 
 
```
ifconfig eth0 down
```
```
ifconfig eth0 hw ether 00:01:02:03:04:05
```
 
 
***[COLOR=red]Ports in use[/COLOR]***
 
#Listening on open ports:
```
netstat -an | grep LISTEN
```
 
# lists all Internet connections
```
lsof -i
```
 
# displays list of open sockets (use apt-get install procinfo)
```
socklist
```
```
netstat -anp --udp --tcp | grep LISTEN
```
 
# List active connections to/from system
```
netstat -tup
```
 
# List listening ports from system
```
netstat -tupl
```
 
 
***[COLOR=red]Firewall (iptables)[/COLOR]***
 
# For status
```
iptables -L -n -v
```
 
# Open everything
```
iptables -P INPUT       ACCEPT
```
```
iptables -P FORWARD     ACCEPT
```
```
iptables -P OUTPUT      ACCEPT
```
 
# Zero the packet and byte counters in all chains
```
iptables -Z
```
 
# Flush all chains
```
iptables -F
```
 
# Delete all chains
```
iptables -X
``` 
 
*IP Forward for routing*
 
# Check and then enable IP forward with:
 
# Check IP forward 0=off, 1=on
```
nano -w /proc/sys/net/ipv4/ip_forward
```
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```
 
# or edit /etc/sysctl.conf with:
 
```
net.ipv4.ip_forward = 1
```
 
 
***[COLOR=red]NAT Network Address Translation[/COLOR]***
 
# to activate NAT
```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```
 
# Port forward 20022 to internal IP port ssh
```
iptables -t nat -A PREROUTING -p tcp -d 78.31.70.238 --dport 20022 -j DNAT --to 192.168.16.44:22
```
 
# Port forward of range 993-995
```
iptables -t nat -A PREROUTING -p tcp -d 78.31.70.238 --dport 993:995 -j DNAT --to 192.168.16.254:993-995
```
 
```
ip route flush cache
```
 
# Check NAT status
```
iptables -L -t nat
``` 
 
 
NOTE: You can delete a port forward with -D instead of -A.
 
 
***[COLOR=red]DNS[/COLOR]***
 
On *nix the DNS entries are valid for all interfaces and are stored in /etc/resolv.conf. 
The domain to which the host belongs is also stored in this file. A minimal configuration is:
 
```
nameserver 78.31.70.238
search mydomain.net intern.lab
domain mydomain.net
```
 
 
Check the system domain name with:
 
# Same as dnsdomainname
```
hostname -d
```
 
 
***[COLOR=red]Forward queries[/COLOR]***
 
Dig is used to test the DNS settings.
See from which server the client receives the answer (simplified answer).
in this example, we use google.com
 
dig google.com
google.com.267INA64.233.187.99 
;; SERVER: 192.168.1.254#53(192.168.1.254)
 
 
The router 192.168.1.254 answered and the response is the A entry. 
Any entry can be queried and the DNS server can be selected with @:
 
# To test the local server
```
dig @127.0.0.1 NS sun.com
```
 
# Query an external server
```
dig @204.97.212.10 NS MX heise.de
```
 
# Get the full zone (zone transfer)
```
dig AXFR @ns1.xname.org cb.vu
```
 
 
The program host is also quite powerful.
 
# Get the mail MX entry
```
host -t MX google.com
```
 
# Get the NS record over a TCP connection
```
host -t NS -T google.com
```
 
# Get everything
```
host -a google.com 
```
 
 
 
***[COLOR=red]Reverse queries[/COLOR]***
 
Find the name belonging to an IP address (in-addr.arpa.). This can be done with dig, host and nslookup:
 
```
dig -x 78.31.70.238
```
```
host 78.31.70.238
```
```
nslookup 78.31.70.238
```
 
 
Single hosts can be configured in the file /etc/hosts instead of running named locally 
to resolve the hostname queries. The format is simple, for example:
 
64.233.187.99 google.com google
 
 
***[COLOR=red]DHCP[/COLOR]***
 
The default ubuntu dhcp client is dhclient, however, i like dhcpcd a lot better, 
and that is what i will use in my examples
 
apt-get install dhcpcd to install it.
 
# Trigger a renew (does not always work)
```
dhcpcd -n eth0
```
 
# release and shutdown
```
dhcpcd -k eth0
``` 
 
 
The lease with the full information is stored in:
 
/var/lib/dhcpcd/dhcpcd-eth0.info
 
 
For dhclient:
 
```
dhclient eth0
```
 
 
The lease with the full information is stored in:
 
/var/db/dhclient.leases.eth0
 
 
Use 
 
/etc/dhclient.conf
 
to prepend options or force different options:
 
```
nano -w /etc/dhclient.conf
```
 
interface "eth0" {
prepend domain-name-servers 127.0.0.1;
default domain-name "google.com";
supersede domain-name "google.com";
}
 
 
***[COLOR=red]Traffic analysis[/COLOR]***
 
Bmon *[http://people.suug.ch/~tgr/bmon/](http://people.suug.ch/~tgr/bmon/)* is a small console bandwidth monitor and can display the 
flow on different interfaces. You can install it on ubuntu with apt-get install bmon
 
Sniff with tcpdump (tcpdump comes with ubuntu)
 
```
tcpdump -nl -i eth0 not port ssh and src \(192.168.16.121 or 192.168.16.54\)
```
 
# select to/from a single IP
```
tcpdump -n -i eth0 net 192.168.16.121
``` 
 
# select traffic to/from a network
```
tcpdump -n -i eth0 net 192.168.16.0/24
```
 
# Buffered output
```
tcpdump -l > dump && tail -f dump
``` 
 
# Write traffic headers in binary file 
```
tcpdump -i eth0 -w traffic.eth0
```
 
# Write traffic + payload in binary file
```
tcpdump -i eth0 -s 0 -w traffic.eth0
```
 
# Read from file (also for ethereal
```
tcpdump -r traffic.eth0
```
 
# The two classic commands 
```
tcpdump port 80
```
 
# Check if pop or imap is secure 
```
tcpdump host google.com
```
 
```
tcpdump -i eth0 -X port \(110 or 143\)
```
 
# Only catch pings
```
tcpdump -n -i eth0 icmp
```
 
# -s 0 for full packet -A for ASCII
```
tcpdump -i eth0 -s 0 -A port 80 | grep GET
```
 
 
*Additional important options:*
 
 
* -A Print each packets in clear text (without header)
 
* -X Print packets in hex and ASCII
 
* -l Make stdout line buffered
 
* -D Print all interfaces available
 
***[COLOR=red]Scan with nmap[/COLOR]***
 
Nmap [http://insecure.org/nmap/](http://insecure.org/nmap/) is a port scanner with OS detection, 
it is usually installed on most distributions. Install it in ubuntu
with apt-get install nmap
 
# scans all reserved TCP ports on the host
```
nmap google.com
```
 
# Find out which IP are used and by which host on 0/24
```
nmap -sP 192.168.16.0/24
```
 
# Do a stealth SYN scan with version and OS detection
```
nmap -sS -sV -O google.com
``` 
 
 
Other non standard but useful tools are hping ([www.hping.org]("http://www.hping.org")) an IP packet assembler/analyzer 
and fping (fping.sourceforge.net). fping can check multiple hosts in a round-robin fashion.
 
***[COLOR=red]Traffic control (QoS)[/COLOR]***
 
Traffic control manages the queuing, policing, scheduling, and other traffic parameters for a network. 
The following examples are simple practical uses of the Linux capabilities to better use the available 
bandwidth.
 
*Limit upload*
 
DSL or cable modems have a long queue to improve the upload throughput. 
However filling the queue with a fast device (e.g. ethernet) will dramatically 
decrease the interactivity. It is therefore useful to limit the device 
upload rate to match the physical capacity of the modem, this should 
greatly improve the interactivity. Set to about 90% of the modem maximal (cable) speed.
 
For a 512 Kbit upload modem:
 
```
tc qdisc add dev eth0 root tbf rate 480kbit latency 50ms burst 1540
```
 
# Status
```
tc -s qdisc ls dev eth0
``` 
 
# Delete the queue 
```
tc qdisc del dev eth0 root
```
 
[code[tc qdisc change dev eth0 root tbf rate 220kbit latency 50ms burst 1540[/code]
 
 
***[COLOR=red]Quality of service[/COLOR]***
 
Priority queuing with tc to optimize VoIP. See the full example on voip-info.org or 
[www.howtoforge.com]("http://www.howtoforge.com"). Suppose VoIP uses udp on ports 10000:11024 and device eth0 
(could also be ppp0 or so). The following commands define the QoS to three queues 
and force the VoIP traffic to queue 1 with QoS 0x1e (all bits set). 
The default traffic flows into queue 3 and QoS Minimize-Delay flows into queue 2.
 
```
tc qdisc add dev eth0 root handle 1: prio priomap 2 2 2 2 2 2 2 2 1 1 1 1 1 1 1 0
```
 
```
tc qdisc add dev eth0 parent 1:1 handle 10: sfq
```
 
```
tc qdisc add dev eth0 parent 1:2 handle 20: sfq
```
 
```
tc qdisc add dev eth0 parent 1:3 handle 30: sfq
```
 
```
tc filter add dev eth0 protocol ip parent 1: prio 1 u32 
```
 
# use server port range (added after u32 above)
```
match ip dport 10000 0x3C00 flowid 1:1
```
 
# or/and use server IP (added after u32 above)
```
match ip dst 123.23.0.1 flowid 1:1
```
 
 
*Status and remove with*
 
# queue status
```
tc -s qdisc ls dev eth0
```
 
# delete all QoS
```
tc qdisc del dev eth0 root
``` 
 
 
*Calculate port range and mask*
 
The tc filter defines the port range with port and mask which you have to calculate. 
Find the 2^# ending of the port range, deduce the range and convert to HEX. 
This is your mask. Example for 10000 -> 11024, the range is 1024.
 
# ending is 2^14 = 16384
```
2^13 (8192) < 10000 < 2^14 (16384)
```
 
# mask is 0x3C00
```
echo "obase=16;(2^14)-1024" | bc
```
 
 
 
***[COLOR=red]NIS Debugging[/COLOR]***
 
Some commands which should work on a well configured NIS client:
 
# get the connected NIS server name (apt-get install nis to use)
```
ypwhich
``` 
 
# The NIS domain name as configured 
```
domainname
``` 
 
# should display the group from the NIS server 
```
ypcat group 
``` 
 
# Rebuild the yp database 
```
cd /var/yp && make 
``` 
 
 
Is ypbind running?
 
```
ps auxww | grep ypbind
```
```
/usr/sbin/ypbind   
``` 
```
yppoll passwd.byname
```
 
Map passwd.byname has order number 1190635041. Mon Sep 24 13:57:21 2007
The master server is servername.domain.net.
 
```
nano -w /etc/yp.conf
```
```
ypserver servername
```
```
domain domain.net broadcast
```
 
 
 
***[COLOR=red]Netcat[/COLOR]***
 
Netcat [http://netcat.sourceforge.net](http://netcat.sourceforge.net) (nc) is better known as the "network Swiss Army Knife", 
it can manipulate, create or read/write TCP/IP connections. Here some useful examples, 
there are many more on the net, for example g-loaded.eu[...]
[http://www.g-loaded.eu/2006/11/06/netcat-a-couple-of-useful-examples](http://www.g-loaded.eu/2006/11/06/netcat-a-couple-of-useful-examples) and here 
[http://www.terminally-incoherent.com/blog/2007/08/07/few-useful-netcat-tricks](http://www.terminally-incoherent.com/blog/2007/08/07/few-useful-netcat-tricks).
 
 
***[COLOR=red]File transfer[/COLOR]***
 
Copy a large folder over a raw tcp connection. The transfer is very quick (no protocol overhead) and you don't need to mess up with NFS or SMB or FTP or so, simply make the file available on the server, and get it from the client. Here 192.168.1.1 is the server IP address.
 
# Serve tar folder on port 4444
```
server: tar -cf - -C VIDEO_TS . | nc -l -p 4444 
``` 
 
# Pull the file on port 4444 
```
client: nc 192.168.1.1 4444 | tar xpf - -C VIDEO_TS 
``` 
 
# Server a single file
```
server: cat largefile | nc -l 5678      
``` 
 
# Pull the single file 
```
client: nc 192.168.1.1 5678 > largefile   
``` 
 
# Server partition image 
```
server: dd if=/dev/da0 | nc -l 4444       
``` 
 
# Pull partition to clone 
```
client: nc 192.168.1.1 4444 | dd of=/dev/da0  
``` 
 
# Pull partition to file
```
client: nc 192.168.1.1 4444 | dd of=da0.img  
``` 
 
 
***[COLOR=red]Other hacks[/COLOR]***
 
 
*Remote shell*
 
# Provide a remote shell on port 4444 (aserver backdoor)
```
nc -lp 4444 -e /bin/bash[code] 
 
*Emergency web server*
 
Serve a single file on port 80 in a loop.
 
[code]while true; do nc -l -p 80 < unixtoolbox.xhtml; done
```
 
 
*Chat*
 
Joe and Carter can chat over a simple TCP socket. The text is transferred with the enter key.
 
```
Joe: nc -lp 4444
```
```
Carter: nc 192.168.1.1 4444
```
 
 
AJ

---

### Post by Rocket2DMn on 2008-08-05
Very nice detailed guide for terminal networking.
You have a few code tages that need to be closed at the end (and one or two throughout), just FYI.  You might also consider a little table of contents at the top and bigger, bolder subtitles on sections.
Good work.

---

### Post by ajmorris on 2008-08-05
> **Rocket2DMn said:**
> Very nice detailed guide for terminal networking.
You have a few code tages that need to be closed at the end (and one or two throughout), just FYI. You might also consider a little table of contents at the top and bigger, bolder subtitles on sections.
Good work.
 
Thanks, i was in a hurry when i posted it... i'll start making it easier to read/follow :)

---

### Post by GeneralMao on 2008-08-06
Wow great guide. I have saved it in my bookmark and printed a copy.

Great job, very handy.

---

### Post by zo934 on 2008-08-06
HEy HOw do I put the firewall back to default, 
I was messing with it lastnight, trying to configure firewall in Ubuntu, 
I think I set it back to default but want to be positive. Now when I try and login, I can login, but all I get is a blank screen, and i have to power down my machine, could I have changed something in the firewall to cause this? Help please

---

### Post by eival on 2008-08-06
question about the ToS code.(im not on ubuntu to test right now)

[tc qdisc add dev eth0 root tbf rate 480kbit latency 50ms burst 1540]

for "latency" and "burst"

whats the lowest/fastest time you can set the latency? will it accept 0ms(zero)?

and what is "burst" and what does the number 1540 represent?(packets/ping?)

an if the burst can be changed what would the result be/which would increase speed(setting it higher than 1540 or lower)?

thanks.

---

### Post by ajmorris on 2008-08-08
> **zo934 said:**
> HEy HOw do I put the firewall back to default, 
I was messing with it lastnight, trying to configure firewall in Ubuntu, 
I think I set it back to default but want to be positive. Now when I try and login, I can login, but all I get is a blank screen, and i have to power down my machine, could I have changed something in the firewall to cause this? Help please

I doubt the editing of your firewall will have prevented you from being able to log in, could you please start a new thread, rather than discussing it here, about your issue :)  Feel free to pm me with the link of your thread.

AJ

---

### Post by ajmorris on 2008-08-08
> **eival said:**
> question about the ToS code.(im not on ubuntu to test right now)

[tc qdisc add dev eth0 root tbf rate 480kbit latency 50ms burst 1540]

for "latency" and "burst"

whats the lowest/fastest time you can set the latency? will it accept 0ms(zero)?

and what is "burst" and what does the number 1540 represent?(packets/ping?)

an if the burst can be changed what would the result be/which would increase speed(setting it higher than 1540 or lower)?

thanks.

You must have a latency or limit set. Thus the lowest setting for latency is 1ms.

As for burst, burst is a paramater, similar to the cburst paramater. Essentially, it controls the max amount of data that can be accumulated if the real speed rate is lower than the 'ceil'. By default, it is about 1 packet, in the example, i have set it to 1540 packets. You can also use it in collaboration with ceil to limit speeds when it gets to a certain number of packets, etc.

I hope that helps,

AJ

---

### Post by A_M_S on 2009-09-17
Great compilation.


Thank you!

---

### Post by raja.genupula on 2012-07-17
good thread . its have nice information .

---

