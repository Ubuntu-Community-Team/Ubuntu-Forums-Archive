---
title: "Firestarter problems"
date: 2007-09-18
forum: Server Platforms
---

### Post by delbene on 2007-09-18
I have a problem with Firestarter on my Ubuntu 7.04 laptop: after installing it, my box stops connecting to the internet and becomes much more unresponsive (even if there is no increment in the cpu activity and memory load).

I have two interfaces, eth0 (wired and disconnected) and eth1 (wireless and connected to my router). I set up Firestarter to use eth1 and to be permissive by default.
Traffic is blocked even if the firewall is stopped (it effectively stops, I checked with iptables). If Firestarter is disinstalled, all work again.

To make things difficultier, if I shutdown eth1 and connect by eth0, Firestarter works just fine. :confused:

This is the output of  *sudo iptables -nL* when Firestarter is active:

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  208.67.220.220       0.0.0.0/0           tcp flags:!0x17/0x02 
ACCEPT     udp  --  208.67.220.220       0.0.0.0/0           
ACCEPT     tcp  --  208.67.222.222       0.0.0.0/0           tcp flags:!0x17/0x02 
ACCEPT     udp  --  208.67.222.222       0.0.0.0/0           
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
DROP       0    --  224.0.0.0/8          0.0.0.0/0           
DROP       0    --  0.0.0.0/0            224.0.0.0/8         
DROP       0    --  255.255.255.255      0.0.0.0/0           
DROP       0    --  0.0.0.0/0            0.0.0.0             
DROP       0    --  0.0.0.0/0            0.0.0.0/0           state INVALID 
LSI        0    -f  0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
INBOUND    0    --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.12         208.67.220.220      tcp dpt:53 
ACCEPT     udp  --  192.168.1.12         208.67.220.220      udp dpt:53 
ACCEPT     tcp  --  192.168.1.12         208.67.222.222      tcp dpt:53 
ACCEPT     udp  --  192.168.1.12         208.67.222.222      udp dpt:53 
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
DROP       0    --  224.0.0.0/8          0.0.0.0/0           
DROP       0    --  0.0.0.0/0            224.0.0.0/8         
DROP       0    --  255.255.255.255      0.0.0.0/0           
DROP       0    --  0.0.0.0/0            0.0.0.0             
DROP       0    --  0.0.0.0/0            0.0.0.0/0           state INVALID 
OUTBOUND   0    --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
LSI        0    --  0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
LOG        icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
REJECT     0    --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0 
```and this is the Firestarter config file:

```
#-----------( Firestarter Configuration File )-----------#

# --(External Interface)--
# Name of external network interface
IF="eth1"
# Network interface is a PPP link
EXT_PPP="off"

# --(Internal Interface--)
# Name of internal network interface
INIF="eth0"

# --(Network Address Translation)--
# Enable NAT
NAT="off"
# Enable DHCP server for NAT clients
DHCP_SERVER="off"
# Forward server's DNS settings to clients in DHCP lease
DHCP_DYNAMIC_DNS="on"

# --(Inbound Traffic)--
# Packet rejection method
#   DROP:   Ignore the packet
#   REJECT: Send back an error packet in response
STOP_TARGET="DROP"

# --(Outbound Traffic)--
# Default Outbound Traffic Policy
#   permissive: everything not denied is allowed
#   restrictive everything not allowed is denied
OUTBOUND_POLICY="permissive"

# --(Type of Service)--
# Enable ToS filtering
FILTER_TOS="off"
# Apply ToS to typical client tasks such as SSH and HTTP
TOS_CLIENT="off"
# Apply ToS to typical server tasks such as SSH, HTTP, HTTPS and POP3
TOS_SERVER="off"
# Apply ToS to Remote X server connections
TOS_X="off"
# ToS parameters
#   4:  Maximize Reliability
#   8:  Maximize-Throughput
#   16: Minimize-Delay
TOSOPT=8

# --(ICMP Filtering)--
# Enable ICMP filtering
FILTER_ICMP="off"
# Allow Echo requests
ICMP_ECHO_REQUEST="off"
# Allow Echo replies
ICMP_ECHO_REPLY="off"
# Allow Traceroute requests
ICMP_TRACEROUTE="off"
# Allow MS Traceroute Requests
ICMP_MSTRACEROUTE="off"
# Allow Unreachable Requests
ICMP_UNREACHABLE="off"
# Allow Timestamping Requests
ICMP_TIMESTAMPING="off"
# Allow Address Masking Requests
ICMP_MASKING="off"
# Allow Redirection Requests
ICMP_REDIRECTION="off"
# Allow Source Quench Requests
ICMP_SOURCE_QUENCHES="off"

# --(Broadcast Traffic)--
# Block external broadcast traffic
BLOCK_EXTERNAL_BROADCAST="off"
# Block internal broadcast traffic
BLOCK_INTERNAL_BROADCAST="off"

# --(Traffic Validation)--
# Block non-routable traffic on the public interfaces
BLOCK_NON_ROUTABLES="off"

# --(Logging)--
# System log level
LOG_LEVEL=info
```Other info that could be related:
1) I have also installed tor, and privoxy.
2) I use static IP addressing (192.168.1/24 subnet)
3) My router is a DLink DSL-G624T
4) I use external DNS resolving (opendns) - maybe could be this?

---

### Post by dividebyzero on 2007-09-19
Try this:

Go to Edit->Preference->Network Settings

Under "Internet connected network device", select eth1. Do the same for "Local network connected device". And "Accept".

---

### Post by delbene on 2007-09-20
As I said, I already did this.

> **delbene said:**
> I set up Firestarter to use eth1 and to be permissive by default.

---

### Post by koenn on 2007-09-20
deleted; wrong foot

---

