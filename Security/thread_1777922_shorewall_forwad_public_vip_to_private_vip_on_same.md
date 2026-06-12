---
title: "shorewall forwad public vip to private vip on same box"
date: 2011-06-08
forum: Security
---

### Post by shorif2000 on 2011-06-08
hi,

I am having problems forwarding from public vip to private vip and back

**configuration files**

interfaces
```

#ZONE    INTERFACE    BROADCAST    OPTIONS
net     eth5            detect          
loc     bond0           detect       

```policy
```

#SOURCE    DEST    POLICY        LOG    LIMIT:        CONNLIMIT:
#                LEVEL    BURST        MASK
loc    all    ACCEPT
net    all    ACCEPT        
fw    all    ACCEPT        
#fw    net    ACCEPT        
#all    fw    ACCEPT        

# THE FOLLOWING POLICY MUST BE LAST
all    all    DROP        info
#$FW    net    ACCEPT

```rules
```

#ACTION        SOURCE        DEST        PROTO    DEST    SOURCE        ORIGINAL    RATE        USER/    MARK    CONNLIMIT    TIME
#                            PORT    PORT(S)        DEST        LIMIT        GROUP
#SECTION ESTABLISHED
#SECTION RELATED
#SECTION NEW

#ACCEPT loc all tcp 80 #not needed

#    Accept DNS connections from the firewall to the network
#
DNS(ACCEPT)    $FW        net
#
#    Accept SSH connections from the local network for administration
#
SSH(ACCEPT)    loc        all
SSH(ACCEPT)    net        all
SSH(ACCEPT)    $FW        all
#
#    Allow Ping from the local network
#
Ping(ACCEPT)    $FW        all
Ping(ACCEPT)    $FW        all
Ping(ACCEPT)    net        all


#
# Drop Ping from the "bad" net zone.. and prevent your log from being flooded..
#

#Ping(DROP)    net        $FW

ACCEPT        $FW        all        icmp
ACCEPT        loc        all        icmp
ACCEPT        net        all        icmp



#ACCEPT          net           loc:192.168.0.237  tcp  80    -        195.171.205.21
#ACCEPT          net           loc:192.168.0.237  tcp  ssh    -        195.171.205.21


DNAT        net         loc:192.168.0.237  tcp  ssh,80,443            #works




ACCEPT fw net tcp 53     
ACCEPT fw net udp 53  
ACCEPT loc fw tcp 22    

```zones
```

#ZONE    TYPE        OPTIONS        IN            OUT
#                    OPTIONS            OPTIONS
fw    firewall
net    ipv4
loc    ipv4

```masq
```

eth5 bond0 

```In the above my public vip is 195.171.205.21, but i am using a real server ip (192.168.0.237) and it works. BUT if i use 192.168.0.199 which is the private vip on the same box it does not work.

Any help???

---

