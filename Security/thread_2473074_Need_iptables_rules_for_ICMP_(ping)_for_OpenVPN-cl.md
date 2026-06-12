---
title: "Need iptables rules for ICMP (ping) for OpenVPN-client (only for vpn tunnel)"
date: 2022-03-22
forum: Security
---

### Post by han85 on 2022-03-22
Hello!

I need **iptables rules for ICMP (ping)** OpenVPN-client.


I have a question about this.


If I want to maintain a VPN tunnel via OpenVPN by "ping" ICMP iptables rules to be active in both directions?

With this, ping (imcp) is working:   Can ping all ip addresses, also VPN server.
```
iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT 
iptables -A OUTPUT -p icmp --icmp-type echo-reply -j ACCEPT
```

```
iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-reply -j ACCEPT
```



Want only icmp ping on the VPN tunnel connection, but 



with this iptables rules icmp, **isn't working** to ping VPN server.

I can ping other IP addresses but not the VPN server address.

```
iptables -A INPUT -p icmp --icmp-type echo-request -s 0/0 -d $SERVER_IP -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p icmp --icmp-type echo-reply -s $SERVER_IP -d 0/0 -m state --state ESTABLISHED -j ACCEPT
```

```
iptables -A OUTPUT -p icmp --icmp-type echo-request -s $SERVER_IP -d 0/0 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-reply -s 0/0 -d $SERVER_IP -m state --state ESTABLISHED -j ACCEPT
```

[U]Terminal message:
[/U]ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
...


Addendum, I want to use iptables only icmp ping between client and vpn server so that the vpn tunnel is maintained.

I want to block all other icmp ping packets.



All other connections on my machine are ok, no errors.

I have set:
```
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP
```

```
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```

and allowed all other connections individually with iptables.

What's wrong?

Please help, thanks!

---

### Post by #&amp;thj^% on 2022-03-22
I used to use this set up, tailor to your needs:
To enable ICMP ping outgoing request use following iptables rule:

```
SERVER_IP="202.54.10.20"
iptables -A OUTPUT -p icmp --icmp-type 8 -s $SERVER_IP -d 0/0 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

iptables -A INPUT -p icmp --icmp-type 0 -s 0/0 -d $SERVER_IP -m state --state ESTABLISHED,RELATED -j ACCEPT

```
How do I disable outgoing ICMP request?

Use the following rules:

```
iptables -A OUTPUT -p icmp --icmp-type echo-request -j DROP
```

OR

```
iptables -A OUTPUT -p icmp --icmp-type 8 -j DROP
```

ICMP echo-request type will be block by above rule.

You can also get list of ICMP types, just type following command at shell prompt:
```
# /sbin/iptables -p icmp -h
```
And a current VPN ping:
```
ping 10.171.0.6
PING 10.171.0.6 (10.171.0.6) 56(84) bytes of data.
64 bytes from 10.171.0.6: icmp_seq=1 ttl=64 time=0.117 ms
64 bytes from 10.171.0.6: icmp_seq=2 ttl=64 time=0.131 ms
64 bytes from 10.171.0.6: icmp_seq=3 ttl=64 time=0.133 ms
64 bytes from 10.171.0.6: icmp_seq=4 ttl=64 time=0.131 ms
64 bytes from 10.171.0.6: icmp_seq=5 ttl=64 time=0.166 ms
64 bytes from 10.171.0.6: icmp_seq=6 ttl=64 time=0.132 ms
64 bytes from 10.171.0.6: icmp_seq=7 ttl=64 time=0.130 ms
64 bytes from 10.171.0.6: icmp_seq=8 ttl=64 time=0.130 ms
64 bytes from 10.171.0.6: icmp_seq=9 ttl=64 time=0.130 ms
64 bytes from 10.171.0.6: icmp_seq=10 ttl=64 time=0.131 ms
64 bytes from 10.171.0.6: icmp_seq=11 ttl=64 time=0.133 ms
64 bytes from 10.171.0.6: icmp_seq=12 ttl=64 time=0.134 ms
^C
--- 10.171.0.6 ping statistics ---
12 packets transmitted, 12 received, 0% packet loss, time 11145ms
rtt min/avg/max/mdev = 0.117/0.133/0.166/0.010 ms

```
Last EDIT:
 You can add the following rule in order to block pings to and from the server on a specific machine. The command will print an error message when you run the ping command:

```
sudo iptables -A INPUT -p icmp --icmp-type echo-request -j REJECT
```

---

### Post by han85 on 2022-03-23
@ 1fallen, which iptables rule for icmp ping is needed to get a VPN tunnel upright for icmp ping?

Does the VPN server ping the client (me) or
does the OpenVPN client ping the VPN server to maintain the VPN tunnel? Or ping both?

INPUT (icmp) rule or OUTPUT (icmp) rule? or both?

---

### Post by han85 on 2022-03-23
I have tested these iptables rules before.

```
SERVER_IP="MY-VPN-SERVER-IP-HERE"
iptables -A OUTPUT -p icmp --icmp-type 8 -s $SERVER_IP -d 0/0 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

iptables -A INPUT -p icmp --icmp-type 0 -s 0/0 -d $SERVER_IP -m state --state ESTABLISHED,RELATED -j ACCEPT
```


[U]Terminal message:
[/U]ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
...
I am really desperate to find out what the problem is.


With the following iptables icmp rule it works, but I don't want this in my iptables.

```
$IPT -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT
$IPT -A INPUT -p icmp --icmp-type echo-reply -j ACCEPT
```


_Terminal message:_
PING my-vpn-server-ip-here (my-vpn-server-ip-here) 56(84) bytes of data.
64 bytes from my-vpn-server-ip-here: icmp_seq=1 ttl=58 time=30.7 ms
64 bytes from my-vpn-server-ip-here: icmp_seq=2 ttl=58 time=28.1 ms
64 bytes from my-vpn-server-ip-here: icmp_seq=3 ttl=58 time=28.4 ms
64 bytes from my-vpn-server-ip-here: icmp_seq=4 ttl=58 time=28.4 ms

--- my-vpn-server-ip-here ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms

---

### Post by han85 on 2022-03-23
Did a test with icmp iptables rules:

That is working, but no idea if you can put it in my iptables like this.

SERVER_IP="MY-VPN-SERVER-IP-HERE"

```
iptables -A OUTPUT -p icmp --icmp-type echo-request -d $SERVER_IP -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-reply -s $SERVER_IP -j ACCEPT
```
[U]
Terminal message:

[/U]```
$ping my-vpn-server-ip-here
PING my-vpn-server-ip-here (my-vpn-server-ip-here) 56(84) bytes of data.
64 bytes from my-vpn-server-ip-here: icmp_seq=1 ttl=58 time=30.0 ms
64 bytes from my-vpn-server-ip-here: icmp_seq=2 ttl=58 time=28.0 ms
64 bytes from my-vpn-server-ip-here: icmp_seq=3 ttl=58 time=28.1 ms
64 bytes from my-vpn-server-ip-here: icmp_seq=4 ttl=58 time=28.1 ms
64 bytes from my-vpn-server-ip-here: icmp_seq=5 ttl=58 time=28.1 ms

--- my-vpn-server-ip-here ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4005ms
```

---

### Post by han85 on 2022-03-23
Further test.

With this iptables icmp rule I DO NOT get **any ping: sendmsg: Operation not permitted message**

```
iptables -A OUTPUT -o $INET -j ACCEPT -d $SERVER_IP -s $HOST_IP/24 -p icmp --icmp-type echo-request
iptables -A INPUT -i $INET -j ACCEPT -s $HOST_IP/24 -d 190.2.131.200 -p icmp --icmp-type echo-reply
```


**but the ping gets stuck.**

ping **my-vpn-server-ip-here**
PING **my-vpn-server-ip-here** (**my-vpn-server-ip-here**) 56(84) bytes of data.

--- my-vpn-server-ip-here ping statistics ---
13 packets transmitted, 0 received, 100% packet loss, time 12289ms

hmm...

---

### Post by #&amp;thj^% on 2022-03-23
This is going to be a very long post, so take your time, and remember cooler heads prevail. ;)
Please don't get frustrated, There are some tools that will be helpful in trying to visualize the traffic and testing which path traffic follows, namely these;
[list]
    [*]TCPdump - Linux command line tool to visualize network packets
    [*]WireShark - Windows GUI tool to visualize network packets
    [*]ping - Testing tool to determine if a message can be sent back and forth between source and destination
    [*]traceroute - Similar to the above but tries to determine every hop between the source and the target destination[/list]

With these tools it's possible to send test packets of information over a connection from one system to the other, and to see these packets appear on the screen and to see where they are coming from (source address), and where they are going to (destination address). 
If you are unable to connect to the remote private subnet, make sure that the proper access is delegated inside Access Server. (e.g. Make sure your local subnets are listed under VPN Settings, and under the Specify the private subnets to which all clients should be given access (as 'network/netmask_bits', one per line): textbox.) If you are using the Yes, using routing (advanced) option, make sure that you have added the proper static routes on your local router. If you do not know how to or cannot do this, it is preferable that you use the default Yes, using NAT option. If you are using the NAT option, make sure that you DO NOT list your subnets inside the Advanced VPN section, under the Private Routed Subnets.
On the test ping I showed you it was from Client to VPN.

NOTE: If the target server is also a Linux system, you can run TCPdump there as well.

This is a fairly simple situation. In **MY example** our OpenVPN client has VPN IP address 172.27.232.4 and the Access Server itself has IP address 192.168.47.133, and the target server we're trying to reach has IP address 192.168.47.252. Let's assume that you have configured the OpenVPN Access Server properly and it is currently configured in VPN Settings to give access to 192.168.47.252/32 via the yes, using routing (advanced) method. Let's also assume that the subnet in your local network is a different one from the one used where the Access Server is. We're assuming that you've gone through the checklist above and that none of the problems mentioned there apply, but that you are still unable to reach the purple target server. Let's start our tests. 

On one terminal I'll use:
```
sudo tcpdump -eni any icmp

```
I then will open another Tab in terminal and ping from there, while leaving the other open:
```
ping 192.168.x.xx
```
it should now show both outputs:
EG:
```
PING 192.168.1.32 (192.168.1.32) 56(84) bytes of data.
64 bytes from 192.168.1.32: icmp_seq=1 ttl=64 time=0.088 ms
64 bytes from 192.168.1.32: icmp_seq=2 ttl=64 time=0.083 ms
64 bytes from 192.168.1.32: icmp_seq=3 ttl=64 time=0.084 ms
64 bytes from 192.168.1.32: icmp_seq=4 ttl=64 time=0.147 ms
64 bytes from 192.168.1.32: icmp_seq=5 ttl=64 time=0.146 ms
64 bytes from 192.168.1.32: icmp_seq=6 ttl=64 time=0.136 ms
64 bytes from 192.168.1.32: icmp_seq=7 ttl=64 time=0.142 ms
**[COLOR="#FF0000"]64 bytes from 192.168.1.32: icmp_seq=8 ttl=64 time=0.145 ms[/COLOR]**
64 bytes from 192.168.1.32: icmp_seq=9 ttl=64 time=0.144 ms
64 bytes from 192.168.1.32: icmp_seq=10 ttl=64 time=0.142 ms
64 bytes from 192.168.1.32: icmp_seq=11 ttl=64 time=0.083 ms
^C
--- 192.168.1.32 ping statistics ---
11 packets transmitted, 11 received, 0% packet loss, time 10123ms
rtt min/avg/max/mdev = 0.083/0.121/0.147/0.028 ms

```
and:
```
sudo tcpdump -eni any icmp
tcpdump: data link type LINUX_SLL2
tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
listening on any, link-type LINUX_SLL2 (Linux cooked v2), snapshot length 262144 bytes
11:34:07.240247 tun0  Out ifindex 7 ethertype IPv4 (0x0800), length 100: 10.84.0.6 > 10.84.0.1: ICMP host 10.84.0.6 unreachable - admin prohibited filter, length 60
11:34:34.351740 lo    In  ifindex 1 00:00:00:00:00:00 ethertype IPv4 (0x0800), length 104: 192.168.1.32 > 192.168.1.32: ICMP echo request, id 1, seq 1, length 64
11:34:34.351767 lo    In  ifindex 1 00:00:00:00:00:00 ethertype IPv4 (0x0800), length 104: 192.168.1.32 > 192.168.1.32: ICMP echo reply, id 1, seq 1, length 64
11:34:35.354774 lo    In  ifindex 1 00:00:00:00:00:00 ethertype IPv4 (0x0800), length 104: 192.168.1.32 > 192.168.1.32: ICMP echo request, id 1, seq 2, length 64
11:34:35.354800 lo    In  ifindex 1 00:00:00:00:00:00 ethertype IPv4 (0x0800), length 104: 192.168.1.32 > 192.168.1.32: ICMP echo reply, id 1, seq 2, length 64
11:34:36.368119 lo    In  ifindex 1 00:00:00:00:00:00 ethertype IPv4 (0x0800), length 104: 192.168.1.32 > 192.168.1.32: ICMP echo request, id 1, seq 3, length 64
11:34:36.368146 lo    In  ifindex 1 00:00:00:00:00:00 ethertype IPv4 (0x0800), length 104: 192.168.1.32 > 192.168.1.32: ICMP echo reply, id 1, seq 3, length 64
11:34:37.381686 lo    In  ifindex 1 00:00:00:00:00:00 ethertype IPv4 (0x0800), length 104: 192.168.1.32 > 192.168.1.32: ICMP echo request, id 1, seq 4, length 64
11:34:37.381729 lo    In  ifindex 1 00:00:00:00:00:00 ethertype IPv4 (0x0800), length 104: 192.168.1.32 > 192.168.1.32: ICMP echo reply, id 1, seq 4, length 64
11:34:38.395033 lo    In  ifindex 1 00:00:00:00:00:00 ethertype IPv4 (0x0800), length 104: 192.168.1.32 > 192.168.1.32: ICMP echo request, id 1, seq 5, length 64
11:34:38.395075 lo    In  ifindex 1 00:00:00:00:00:00 ethertype IPv4 (0x0800), length 104: 192.168.1.32 > 192.168.1.32: ICMP echo reply, id 1, seq 5, length 64
11:34:39.408345 lo    In  ifindex 1 00:00:00:00:00:00 ethertype IPv4 (0x0800), length 104: 192.168.1.32 > 192.168.1.32: ICMP echo request, id 1, seq 6, length 64
11:34:39.408385 lo    In  ifindex 1 00:00:00:00:00:00 ethertype IPv4 (0x0800), length 104: 192.168.1.32 > 192.168.1.32: ICMP echo reply, id 1, seq 6, length 64
11:34:40.421776 lo    In  ifindex 1 00:00:00:00:00:00 ethertype IPv4 (0x0800), length 104: 192.168.1.32 > 192.168.1.32: ICMP echo request, id 1, seq 7, length 64
11:34:40.421817 lo    In  ifindex 1 00:00:00:00:00:00 ethertype IPv4 (0x0800), length 104: 192.168.1.32 > 192.168.1.32: ICMP echo reply, id 1, seq 7, length 64
11:34:41.435045 lo    In  ifindex 1 00:00:00:00:00:00 ethertype IPv4 (0x0800), length 104: 192.168.1.32 > [B][COLOR="#FF0000"]192.168.1.32: ICMP echo request, id 1, seq 8, length 64
11:34:41.435087 lo    In  ifindex 1 00:00:00:00:00:00 ethertype IPv4 (0x0800), length 104: 192.168.1.32 > 192.168.1.32: ICMP echo reply, id 1, seq 8, length 64[/COLOR][/B]
11:34:42.448356 lo    In  ifindex 1 00:00:00:00:00:00 ethertype IPv4 (0x0800), length 104: 192.168.1.32 > 192.168.1.32: ICMP echo request, id 1, seq 9, length 64
11:34:42.448397 lo    In  ifindex 1 00:00:00:00:00:00 ethertype IPv4 (0x0800), length 104: 192.168.1.32 > 192.168.1.32: ICMP echo reply, id 1, seq 9, length 64
11:34:43.461713 lo    In  ifindex 1 00:00:00:00:00:00 ethertype IPv4 (0x0800), length 104: 192.168.1.32 > 192.168.1.32: ICMP echo request, id 1, seq 10, length 64
11:34:43.461754 lo    In  ifindex 1 00:00:00:00:00:00 ethertype IPv4 (0x0800), length 104: 192.168.1.32 > 192.168.1.32: ICMP echo reply, id 1, seq 10, length 64
11:34:44.474839 lo    In  ifindex 1 00:00:00:00:00:00 ethertype IPv4 (0x0800), length 104: 192.168.1.32 > 192.168.1.32: ICMP echo request, id 1, seq 11, length 64
11:34:44.474865 lo    In  ifindex 1 00:00:00:00:00:00 ethertype IPv4 (0x0800), length 104: 192.168.1.32 > 192.168.1.32: ICMP echo reply, id 1, seq 11, length 64
11:35:23.018842 tun0  Out ifindex 7 ethertype IPv4 (0x0800), length 100: 10.84.0.6 > 10.84.0.1: ICMP host 10.84.0.6 unreachable - admin prohibited filter, length 60

```
Notice the "seq 8" 
Just like the original packet received and forwarded by the OpenVPN Access Server.
This: "from 192.168.1.32: icmp_seq=8 "

So obviously the packet is making it all the way from the OpenVPN client and through the OpenVPN Access Server on to the network and finally to this target system here. The second line here shows that an echo reply is being sent back. In other words, the target system has received a request to respond, and is doing so now. We can see which MAC address is being used to send out the traffic, and we can correlate this to the correct network interface again. In this case there's only one network interface on the system and it is connected to the network that the Access Server is on as well.

I'm curious to know how long you set the "keepalive" variable.
I've never had to ping mine to keep it running.
Whoosh, Now I need a lunch break. :)

---

### Post by SeijiSensei on 2022-03-23
I use OpenVPN [point-to-point networks]("https://openvpn.net/community-resources/static-key-mini-howto/"). Other than opening the correct UDP port on the remote machine, I haven't had to do anything else. I assumed the keepalive stuff happened over the VPN where I allow all traffic with rules like this:
```

iptables -A INPUT -i tun+ -j ACCEPT
iptables -A FORWARD -i tun+ -o tun+ -j ACCEPT

```

---

### Post by #&amp;thj^% on 2022-03-23
Also to add to SeijiSensei reply, According to the documentation [here]("https://openvpn.net/community-resources/how-to/"), the KeepAlive parameter is probably what you were looking for.
```

    # The keepalive directive causes ping-like
    # messages to be sent back and forth over
    # the link so that each side knows when
    # the other side has gone down.
    # Ping every 10 seconds, assume that remote
    # peer is down if no ping received during
    # a 120 second time period.
    keepalive 10 120
```

This should either be added to the OpenVPN connection profile as a new line, or to the Advanced Configuration on the server (likely /etc/openvpn/openvpn.conf).

---

### Post by han85 on 2022-04-04
Thanks guys,
I'll try it out the days when I have the time.

Question:

Do I only need these iptables rules like you posted before?
```
iptables -A INPUT -i tun+ -j ACCEPT
iptables -A FORWARD -i tun+ -o tun+ -j ACCEPT
```

I currently use these among others:

```
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP
```


```
iptables -A INPUT -i tun+ -j ACCEPT
iptables -A OUTPUT -o tun+ -j ACCEPT
```

and then the iptables rule for INPUT and OUTPUT to the VPN server.

Do I need the OUTPUT iptables rule at all in my case?

Is it better with the INPUT / FORWARD iptables rule you posted before?

---

