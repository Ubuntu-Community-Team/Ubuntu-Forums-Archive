---
title: "iptables DNAT configuration issue with 2 interfaces"
date: 2015-01-03
forum: Security
---

### Post by robuntu2 on 2015-01-03
Hello All,

I am trying to route packets between interfaces on the same machine (Ubuntu server 14.04) to enable MODBUS communication between two networks. My preference would be to get this working using ufw, but reading online it was recommended to learn iptables and then apply this knowledge to ufw, so here I am. I have been trying for the last two days, but as a software developer and not a security guru, I am struggling to get this correctly configured.
The PC has two network interfaces: eth0 and eth1.

Here is my config:
[FONT=arial]eth0 has address 192.168.1.121 (network #1)
eth1 has address 192.168.0.4 (network #2)
MODBUS device is on network #2 at address 192.168.0.97
[/FONT]
The requirement is to be able to send network requests to 192.168.1.121 and have them forwarded to the MODBUS device at address 192.168.0.97 and have the response from this device transparently handled back up to the sender. I understand that I need to use the DNAT (and possibly SNAT) feature of iptables to achieve this. MODBUS communicates on TCP port 502 and UDP port 30718.

Here is what I have so far:
```
iptables -t nat -A PREROUTING -p tcp --dport 502 -j DNAT --to-destination 192.168.0.97:502
iptables -t nat -A PREROUTING -p udp --dport 30718 -j DNAT --to-destination 192.168.0.97:30718

```

I haven't specified a source IP address above as any MODBUS request sent to 192.168.1.121 on eth0 should be serviced. I have tried various iptables nat POSTROUTING configs (and read much of the excellent tutorial on iptables DNAT configuration at [www.frozentux.net]("http://www.frozentux.net")), but am honestly guessing at this point. What eludes me in particular is how the request is routed from eth0 (192.168.1.121) to eth1 internally and then back out on the wire to the MODBUS device - it's not at all clear to me what represents source & destination addresses for these packets on their journey to the MODBUS device.

Any help and guidance would be much appreciated!

rob

---

### Post by Doug S on 2015-01-03
Hi and welcome to Ubuntu forums,

I would specify the interface for this type of port forwarding:```
iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 502 -j DNAT --to-destination 192.168.0.97:502
iptables -t nat -A PREROUTING -p udp -i eth0 --dport 30718 -j DNAT --to-destination 192.168.0.97:30718
```You also need to have forwarding enabled. Example:```
doug@doug-64:~/init$ [COLOR=#ff0000]cat /proc/sys/net/ipv4/ip_forward[/COLOR]
1
```Now, you also need to be sure you have the rest of the forward path enabled in iptables. This might be achieved via default policy, or you might specifically have to allow it. On my system the default is DROP, so I have to specifically allow:```
iptables -A FORWARD -i eth0 -o eth1 -p tcp --dport 502 -j ACCEPT
iptables -A FORWARD -i eth0 -o eth1 -p udp --dport 30718 -j ACCEPT
```Also, you need to provide a return path, which again depends on your default policy.```
iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT
```And I think (but am not sure for your case. In my case I always have it anyhow) you need an SNAT in the return path:```
iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to [FONT=arial]192.168.1.121[/FONT]
```Let us know if this helps.

---

### Post by robuntu2 on 2015-01-03
Doug - many thanks for the detailed response! Trying it now... :-)

---

### Post by robuntu2 on 2015-01-03
Doug,

I gave it a whirl, but still no joy. I flushed and entered the commands provided with no errors. A question I have is: don't we also need to add a FORWARD between interfaces for the UDP protocol as you provided for the TCP protocol on dport 502?

ie.
```
iptables -A FORWARD -i eth0 -o eth1 -p udp --dport 30718 -j ACCEPT
```

I would appreciate your thoughts.

Thanks,

rob

---

### Post by Doug S on 2015-01-03
> **robuntu2 said:**
> A question I have is: don't we also need to add a FORWARD between interfaces for the UDP protocol as you provided for the TCP protocol on dport 502?Yes. I only gave one of lines needed, and thought you would figure out that the other was also needed. I'll add it to my original post for other readers ( I have a habit of underestimating how long a reply will take and then I scramble as I am out of time).

Could you post the output for these two commands:

EDIT: AFTER attempts to use it. i.e. I want to observe the packet counters.```
sudo iptables -v -x -n -L
sudo iptables -t nat -v -x -n -L
```

---

### Post by robuntu2 on 2015-01-03
Doug - I tried with the config provided and still no joy. I will provide the packet counter info shortly... (I had to step out for a while)

---

### Post by robuntu2 on 2015-01-03
Doug - here's the output from the commands you provided...

```
sudo iptables -v -x -n -L
Chain INPUT (policy ACCEPT 34 packets, 3463 bytes)
    pkts      bytes target     prot opt in     out     source               destination         


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
     484    30272 ACCEPT     tcp  --  eth0   eth1    0.0.0.0/0            0.0.0.0/0            tcp dpt:502
       0        0 ACCEPT     udp  --  eth0   eth1    0.0.0.0/0            0.0.0.0/0            udp dpt:30718
       0        0 ACCEPT     all  --  eth1   eth0    0.0.0.0/0            0.0.0.0/0           


Chain OUTPUT (policy ACCEPT 22 packets, 1848 bytes)
    pkts      bytes target     prot opt in     out     source               destination         


sudo iptables -t nat -v -x -n -L
Chain PREROUTING (policy ACCEPT 7 packets, 1231 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
      44     2816 DNAT       tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:502 to:192.168.0.97:502
       0        0 DNAT       udp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            udp dpt:30718 to:192.168.0.97:30718


Chain INPUT (policy ACCEPT 7 packets, 1231 bytes)
    pkts      bytes target     prot opt in     out     source               destination         


Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         


Chain POSTROUTING (policy ACCEPT 44 packets, 2816 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 SNAT       all  --  *      eth0    0.0.0.0/0            0.0.0.0/0            to:192.168.1.121


```

I'm sure I'm not understanding this correctly, but a couple of things seem odd:
- How can the FORWARD section be dealing with 484 packets when INPUT only received 34 in total?
- I see no UDP packets on the FORWARD or nat PREROUTING chains.

Is it possible that I need to manage connection state for this communication? I could use wireshark to see what happens when the initial connection request comes through on 502 ... maybe the device side attempts to open a UDP transmission to the source.

Thanks again for the guidance.

rob

---

### Post by Doug S on 2015-01-03
> **robuntu2 said:**
> I'm sure I'm not understanding this correctly, but a couple of things seem odd:
- How can the FORWARD section be dealing with 484 packets when INPUT only received 34 in total?That is correct. The prerouting chain will only be traversed once per connection, as thereafter, and for the same connection, the prerouting chain is bypassed and the connection tracking knows what to do.> **robuntu2 said:**
> - I see no UDP packets on the FORWARD or nat PREROUTING chains.Yes, that seems odd, based on what you described.> **robuntu2 said:**
> Is it possible that I need to manage connection state for this communication?You shouldn't have to, but I could well be wrong. Note that I have less experience with UDP forwarding, but lots with TCP forwarding.> **robuntu2 said:**
> I could use wireshark to see what happens when the initial connection request comes through on 502 ... maybe the device side attempts to open a UDP transmission to the source.Yes, tcpdump, or wireshark, as you seem to prefer, is for sure the next step. Let's observe, at the packet level what is happening on both eth0 and eth1.

Currently the tcp part forward seems to be working, but there is no return packets. Easy to confirm or deny via packet sniffing.

EDIT 1: Note that since all of your default policies are ACCEPT, you don't actually need the specific FORWARD rules. However, they are currently providing useful information.

EDIT 2: It might also help to start adding some logging lines to the tables. For example, I have made good use of this on occasions:```
#
# following is for debug only. Normally commented out.
#iptables -t nat -A POSTROUTING -j LOG --log-prefix "NAT_POST" --log-level info
```

---

### Post by robuntu2 on 2015-01-03
Doug - I appreciate the feedback.

I just completed checking the comms with Wireshark. It seems that UDP is only used for a particular piece of client software from GE, and that typically TCP on port 502 is all that we should need for pure MODBUS (I will eventually need the UDP port comms once I have this working via my regular application, at which point I'll see if I can get the GE software to connect).

Can I enter the line to enable logging at the CL or does this need to be in a file of sorts?

I will do a dump and provide feedback. Right now heading out to a function, so will probably only get to this tomorrow.

I (very much) appreciate the help!

rob

---

### Post by Doug S on 2015-01-03
> **robuntu2 said:**
> Can I enter the line to enable logging at the CL or does this need to be in a file of sorts?Yes it can be on the CL, my example was copied and pasted from my iptables script. Obviously things that log so many packets are just for debugging, otherwise you can end up with huge logs files.

---

### Post by robuntu2 on 2015-01-04
Doug

OK, started tcpdump on both eth0 and eth1, then ran my app to make a couple of attempts to connect to the MODBUS device. I did inspect the dumps using wireshark, but I see little besides the general networking noise and the inbound connection attempts on port 502.
To recap - My PC (client) IP is 192.168.1.175 and attempts to connect to the server on eth0 at 192.168.1.121. The 2nd server NIC (eth1) is 192.168.0.4 which has access to the MODBUS device at 192.168.0.97 on the 192.168.0.x network.

Attached are the dumps for eth0 and eth1. Both of them are .pcap (I couldn't preserve the extensions with the file upload manager). I hope that they make (much) more sense to you than they do to me. "Network-land" vs "software-development-land" is rather scary. I hope they pay you guys well. ;)

I would appreciate your thoughts when you have a moment.

Thanks,

rob

---

### Post by Doug S on 2015-01-04
As I thought yesterday, it seems to be working fine in terms of properly forwarding the packets to 192.168.0.97. However 192.168.0.97 never answers back.

You will have to tell us more about your network. How does 192.168.0.97 communicate with the world? (or does it?) Is there a router somewhere on the 192.168.0.X sub-net? I suspect that packets from 192.168.0.97 destined for 192.168.1.175 do not know to use 192.168.0.4 as the gateway. OR, for whatever reason it just doesn't respond at all.

Is there such a thing as a routing table on a MODBUS device? I.E. can it be told to route packets for the 192.168.1.X sub-net using 192.168.0.4 as the gateway?

I'll think about if we can SNAT both directions such that on the 192.168.0.X side the packets appear to have come from 192.168.0.4. This is something I have never tried before. Maybe we can turn things around and still get away with one SNAT (I don't think so). I'll need to think about this some. Some experimenting might be required.

I am pretty good with iptables, but a little weak in routing, if other readers care to chime in.

Edit: Is there any way to determine if 192.168.0.97 is responding? Or that it knows someone is trying to establish a tcp connection? I think we need that answer first.

---

### Post by robuntu2 on 2015-01-04
> **Doug S said:**
> As I thought yesterday, it seems to be working fine in terms of properly forwarding the packets to 192.168.0.97. However 192.168.0.97 never answers back.

You will have to tell us more about your network. How does 192.168.0.97 communicate with the world? (or does it?) Is there a router somewhere on the 192.168.0.X sub-net? I suspect that packets from 192.168.0.97 destined for 192.168.1.175 do not know to use 192.168.0.4 as the gateway. OR, for whatever reason it just doesn't respond at all.

Is there such a thing as a routing table on a MODBUS device? I.E. can it be told to route packets for the 192.168.1.X sub-net using 192.168.0.4 as the gateway?

I'll think about if we can SNAT both directions such that on the 192.168.0.X side the packets appear to have come from 192.168.0.4. This is something I have never tried before. Maybe we can turn things around and still get away with one SNAT (I don't think so). I'll need to think about this some. Some experimenting might be required.

I am pretty good with iptables, but a little weak in routing, if other readers care to chime in.

Edit: Is there any way to determine if 192.168.0.97 is responding? Or that it knows someone is trying to establish a tcp connection? I think we need that answer first.

Doug,

Thanks for the feedback. 

The PC has two interfaces: 
eth0/192.168.1.121 is used to communicate with the outside world; has a static IP, has a gateway address configured, and is connected to a regular (unmanaged) switch by which it reaches the Internet.
eth1/192.168.0.4 is used to communicate on the internal plant network; has a static IP but no gateway address configured, and is connected to another regular unmanaged switch to communicate with devices on this internal plant network.
The PLC (MODBUS device) is a TCP/IP enabled device. When I run my application directly on the PC, it happily communicates with the PLC. When I try to reach it externally through eth0, it's a no-go.
There are no routers etc involved in this besides the router/switch that provides network access to eth0 on the PC.

My sense is that what we need to do is masquerade all the way through, ie. when we direct the packet out through eth1, it must look as though it comes from 192.168.0.4 otherwise that network doesn't know how to route it back to eth1's IP since there is no gateway configured for that network.

Thanks again for your continued input.

Regards,

rob

---

### Post by Doug S on 2015-01-04
Can you confirm or deny that 192.168.0.97 knows that 192.168.1.175 is trying to establish a tcp connection? i.e. can you confirm or deny that 192.168.0.97 is sending a tcp ack packet, but it is going astray?
Will you always be coming from 192.168.1.175? As we might need to hard code the return path (not sure yet). Both directions SNAT is a bit messy, or so I think (and some references I have found seem to concur).
Anyway, I'll be back shortly with a brute force suggestion.

---

### Post by robuntu2 on 2015-01-04
Doug - no, I can't confirm that. I can only confirm that 192.168.0.97 can respond happily to requests from 192.168.0.4.

And no, this is a temporary solution used cautiously (but regularly) to reach into the internal plant network from the outside to perform configuration. The idea would be to create a script of what iptables config needs to be applied, and apply this at the time access is needed. For obvious reasons, we can't do this on a permanent basis as it exposes the internal plant network to the hazards of the outside world...

rob

---

### Post by HermanAB on 2015-01-04
BTW, it may be easiest to use socat to hook things together:

socat(1)                                                                                               socat(1)

NAME
       socat - Multipurpose relay (SOcket CAT)

SYNOPSIS
       socat [options] <address> <address>
       socat -V
       socat -h[h[h]] | -?[?[?]]
       filan
       procan

DESCRIPTION
       Socat is a command line based utility that establishes two bidirectional byte streams and transfers data
       between them. Because the streams can be constructed from a large set of different types of  data  sinks
       and  sources  (see  address  types),  and because lots of address options may be applied to the streams,
       socat can be used for many different purposes.

---

### Post by Doug S on 2015-01-05
I am not familiar with socat. Rob let us know if you want to try that route.
I am not sure this will work, but I do know it loads and the syntax seems O.K. It might need some tweaks for your particular situation:```
#!/bin/sh
FWVER=0.01
#
# robuntu2_dnat 2015.01.04 Ver:0.01
#     Attempt to provide external access
#     to a MODBUS device.
#
# edit for addresses and run as sudo
#

echo "Loading robuntu2_dnat version $FWVER..\n"

# The location of the iptables program
#
IPTABLES=/sbin/iptables

#Setting the EXTERNAL and INTERNAL interfaces and addresses for the network
#
EXTIF="eth0"
INTIF="eth1"
EXTIP="192.168.1.121"
INTIP="192.168.0.4"
EXTDEST="192.168.1.175"
INTDEST="192.168.0.97"
UNIVERSE="0.0.0.0/0"

echo "  External Interface: $EXTIF  Internal Interface: $INTIF  External IP: $EXTIP  Internal IP: $INTIP  External Destination: $EXTDEST  Internal Destination: $INTDEST"

#CRITICAL:  Enable IP forwarding since it is disabled by default
#
echo Enabling forwarding...
echo "1" > /proc/sys/net/ipv4/ip_forward

#Clearing any previous configuration
#
echo "  Clearing any existing rules and setting default policy to ACCEPT.."
$IPTABLES -P INPUT ACCEPT
$IPTABLES -F INPUT
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -F OUTPUT
$IPTABLES -P FORWARD ACCEPT
$IPTABLES -F FORWARD
$IPTABLES -t nat -F
# Delete user defined chains
$IPTABLES -X
# Reset all IPTABLES counters
$IPTABLES -Z
# While my references do not have it, I think this is needed.
$IPTABLES -t nat -Z

$IPTABLES -t nat -A PREROUTING -p tcp -i $EXTIF --dport 502 -j DNAT --to-destination $INTDEST:502
$IPTABLES -t nat -A PREROUTING -p udp -i $EXTIF --dport 30718 -j DNAT --to-destination $INTDEST:30718
$IPTABLES -t nat -A PREROUTING -p tcp -i $INTIF --sport 502 -j DNAT --to-destination $EXTDEST
$IPTABLES -t nat -A PREROUTING -p udp -i $INTIF --sport 30718 -j DNAT --to-destination $EXTDEST

# The FORWARD rules are only needed if the default policy is not ACCEPT
#$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -p tcp --dport 502 -j ACCEPT
#$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -p udp --dport 30718 -j ACCEPT
#$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT

$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j SNAT --to $EXTIP
$IPTABLES -t nat -A POSTROUTING -o $INTIF -j SNAT --to $INTIP

echo robuntu2_dnat $FWVER done.
```

---

### Post by robuntu2 on 2015-01-05
Herman - thanks for the recommendation to try socat, but I'm going to hang in with iptables as I don't think we're far from a solution.

Doug - Thanks for the script. Been a busy day, but home now and about to give it a whirl... Feedback to follow.

Appreciate the help as always!

rob

---

### Post by robuntu2 on 2015-01-05
Doug,

OK, I finally have some joy!

I couldn't get your script to work, BUT after building on some of your previous work, I got the following script to work!

```
iptables -t nat -A PREROUTING -p tcp -i eth0 -m tcp --dport 502 -j DNAT --to-destination 192.168.0.97:502
iptables -t nat -A PREROUTING -p udp -i eth0 -m udp --dport 30718 -j DNAT --to-destination 192.168.0.97:30718


iptables -t nat -A POSTROUTING --out-interface eth0 -j MASQUERADE
iptables -t nat -A POSTROUTING --out-interface eth1 -j MASQUERADE


iptables -A FORWARD --in-interface eth1 -j ACCEPT

```

I *REALLY* appreciate all your help and effort to get this going. I have tested the above config live at one of the customer sites and it works flawlessly.

THANK. YOU. SO. MUCH!!

Regards,

rob

---

### Post by Doug S on 2015-01-05
So glad you got it going.
For certain you do not need the FORWARD line, as the default is to ACCEPT anyhow.
I am curious about a couple of things, but expect you would prefer to move on, rather than play around more.
However,> **robuntu2 said:**
> I couldn't get your script to work,I get it that some things are different than I had in that script, but I was just wondering if it wouldn't even execute for you, or that it did execute but the resulting iptables rule set did not work? If the former, then it might have been just <CR><LF> Verses just <LF> issues, which can be fixed by:```
tr --delete '\r' <robuntu2_dnat >robuntu2_dnat2
```

---

### Post by robuntu2 on 2015-01-06
Doug - it was probably the CR/LF issues. I would have pursued this with you if I didn't arrive at the other solution.

Thanks again for the help!

rob

---

