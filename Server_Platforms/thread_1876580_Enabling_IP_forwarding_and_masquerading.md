---
title: "Enabling IP forwarding and masquerading"
date: 2011-11-06
forum: Server Platforms
---

### Post by adtf01 on 2011-11-06
Hi
 
I am trying to setup a ubuntu server as an internet router.  I have set up the 2 nics, and can access the intenet from the server.  I can see the test client from the server and see the server from the client - can ping both ways.  But I cannot access the internet from the clent.
 
I have created and run nat.sh as per the instruction in the Router documentation.  The code is below.  Any suggestions to help get this thing up and running will be greatly appreciated!
 
echo -e "\n\nLoading simple rc.firewall-iptables version $FWVER..\n"
DEPMOD=/sbin/depmod
MODPROBE=/sbin/modprobe

EXTIF="eth0"
INTIF="eth1"
#INTIF2="eth0"
echo "   External Interface:  $EXTIF"
echo "   Internal Interface:  $INTIF"

#======================================================================
#== No editing beyond this line is required for initial MASQ testing == echo -en "   loading modules: "
echo "  - Verifying that all kernel modules are ok"
$DEPMOD -a
echo "----------------------------------------------------------------------"
echo -en "ip_tables, "
$MODPROBE ip_tables
echo -en "nf_conntrack, " 
$MODPROBE nf_conntrack
echo -en "nf_conntrack_ftp, " 
$MODPROBE nf_conntrack_ftp
echo -en "nf_conntrack_irc, " 
$MODPROBE nf_conntrack_irc
echo -en "iptable_nat, "
$MODPROBE iptable_nat
echo -en "nf_nat_ftp, "
$MODPROBE nf_nat_ftp
echo "----------------------------------------------------------------------"
echo -e "   Done loading modules.\n"
echo "   Enabling forwarding.."
echo "1" > /proc/sys/net/ipv4/ip_forward
echo "   Enabling DynamicAddr.."
echo "1" > /proc/sys/net/ipv4/ip_dynaddr 
echo "   Clearing any existing rules and setting default policy.."

iptables-restore <<-EOF
*nat
-A POSTROUTING -o "$EXTIF" -j MASQUERADE
COMMIT
*filter
:INPUT ACCEPT [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]
-A FORWARD -i "$EXTIF" -o "$INTIF" -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT 
-A FORWARD -i "$INTIF" -o "$EXTIF" -j ACCEPT
-A FORWARD -j LOG
COMMIT
EOF

echo -e "\nrc.firewall-iptables v$FWVER done.\n"

---

### Post by mudasir on 2011-11-06
Hi,

Below is a basic iptables firewall that I use at many places, you can use this or modify this as per your need.

> #!/bin/bash

IPTABLES="/sbin/iptables"
EXTIF="eth0"
INTIF="eth1"


$IPTABLES -P OUTPUT  ACCEPT
$IPTABLES -P INPUT   ACCEPT
$IPTABLES -P FORWARD DROP
ip6tables -L -n > /dev/null 2>&1 && {
  ip6tables -P OUTPUT  ACCEPT
  ip6tables -P INPUT   ACCEPT
  ip6tables -P FORWARD DROP
  ip6tables -A INPUT  -i lo  -j ACCEPT
  ip6tables -A OUTPUT  -o lo  -j ACCEPT
}

cat /proc/net/ip_tables_names | while read table; do
  $IPTABLES -t $table -L -n | while read c chain rest; do
      if test "X$c" = "XChain" ; then
        $IPTABLES -t $table -F $chain
      fi
  done
  $IPTABLES -t $table -X
done

$IPTABLES -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

$IPTABLES -t nat -A POSTROUTING -o $EXTIF  -j MASQUERADE

$IPTABLES -A FORWARD  -i $INTIF  -m state --state NEW  -j ACCEPT
$IPTABLES -A FORWARD  -o $INTIF  -m state --state NEW  -j ACCEPT
$IPTABLES -A FORWARD  -i $EXTIF -m state --state NEW  -j ACCEPT
$IPTABLES -A FORWARD  -o $EXTIF -m state --state NEW  -j ACCEPT

$IPTABLES -A INPUT  -i lo  -m state --state NEW  -j ACCEPT
$IPTABLES -A OUTPUT  -o lo  -m state --state NEW  -j ACCEPT

$IPTABLES -A FORWARD -j LOG

echo 1 > /proc/sys/net/ipv4/ip_forward
echo 1 > /proc/sys/net/ipv4/ip_dynaddr 


---

### Post by koenn on 2011-11-07
check that your server's nic names match the designation you used in the script (eg that eth0 is indeed the nic on the internet side, etc.)

other than that, the script looks OK

what kind of error are you getting when you try to access the internet ?

what do you see when (from the client) you run
```
ping google.com
```
or
```
traceroute ubuntuforums.org
```
(you may have to run this with sudo)

---

### Post by adtf01 on 2011-11-08
> **koenn said:**
> check that your server's nic names match the designation you used in the script (eg that eth0 is indeed the nic on the internet side, etc.)
 
other than that, the script looks OK
 
what kind of error are you getting when you try to access the internet ?
 
what do you see when (from the client) you run
```
ping google.com
```
or
```
traceroute ubuntuforums.org
```
(you may have to run this with sudo)
 
Both give the message thatit cannot be found.  The client machine is a windows machine and the network icon shows there is no internet.

---

### Post by adtf01 on 2011-11-08
Mudasir I have tried your code and when I try to load it I get the message "syntax error Unterminated quote string.
This occurs at the line cat /proc/net/ip_tables_names | while read table; do
and when I comment that line it occurs again at the next line.  
 
Any suggestions?

---

### Post by koenn on 2011-11-08
> **adtf01 said:**
> Both give the message thatit cannot be found.  The client machine is a windows machine and the network icon shows there is no internet.

it helps if you give the exact output, now I don't know whether you have "command not found" or "host not found". 

Try again, with addresses this time : 

```
 traceroute 195.22.138.104
```

---

### Post by adtf01 on 2011-11-09
tracert 195.22.138.104 gives 
1 <1ms  <1ms  <1ms CAJJ 192.168.2.1
2   *         *         *     request timed out and so on for the rest
 
Ping ubuntu.com gives unable to resolve target system name
 
As I said the client is a windows machine and when opening network conntections it indicates that there is a network, but no internet connection, so I am connected to the server, but cannot get beyond to the internet.

---

### Post by adtf01 on 2011-11-09
Ok so I redid the script using [http://ubuntuforums.org/showthread.php?t=119787](http://ubuntuforums.org/showthread.php?t=119787) and it is working.
 
So this is solved thank you
:)

---

