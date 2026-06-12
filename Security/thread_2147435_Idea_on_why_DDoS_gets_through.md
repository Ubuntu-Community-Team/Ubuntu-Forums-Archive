---
title: "Idea on why DDoS gets through?"
date: 2013-05-21
forum: Security
---

### Post by mister3000 on 2013-05-21
Hi, recently my server has been under a UDP flood attack. Even if I tell iptables to drop all UDP packets the attack still lags the network.


I would think my server would be able to withstand the attacks as I have a 1000 Mbit port and the attacks are only around 50-100 Mbit.


When looking at Munin graphs the only thing that spikes during the attack is the network traffic and firewall throughput. The CPU, memory, temperature, disk I/O, etc are barely touched.


[IMG]http://i.imgur.com/FhXUE7B.png[/IMG]


[IMG]http://i.imgur.com/bfxoXwD.png[/IMG]


This is what the attack packets look like:
> 02:28:02.008325 IP 63.238.60.102.snmp > xx.xx.xx.xx:xxxxx:  [P/U/U-0][!init SEQ]_02_04_09_00_00_00_30_17_06_0f_2b_06_01_02_01_0a_12
02:28:02.064812 IP 199.117.179.130.snmp > xx.xx.xx.xx:xxxxx:  [len1468<asnlen8185]
02:28:02.169117 IP 168.126.214.162.snmp > xx.xx.xx.xx:xxxxx:  [len1468<asnlen40909]
02:28:02.273837 IP 199.117.179.130.snmp > xx.xx.xx.xx:xxxxx:  [id?P/x/23]
02:28:02.287917 IP 201.251.244.227.snmp > xx.xx.xx.xx:xxxxx:  [len1468<asnlen42131]
02:28:02.303585 IP 63.225.235.190.snmp > xx.xx.xx.xx:xxxxx:  [len1468<asnlen8169]
02:28:02.331871 IP 61.168.78.186.snmp > xx.xx.xx.xx:xxxxx:  [len1468<asnlen8175]
02:28:02.340145 IP 61.168.78.186.snmp > xx.xx.xx.xx:xxxxx:  [P/U/Bitstring][!init SEQ]_81_28_4e_81_3a_17_81_5a_19_81_05_08_a0_59_02_01_17_30_1d_06_18_2b_06_01_02_01_06_0d_01_03_3d_81_28_4e_81_3a_17_81_5a_19_81_05_08_a0_5c_02_01_17_30_1d_06_18_2b_06_01_02_01_06_0d_01_03
02:28:02.387098 IP 205.171.37.238.snmp > xx.xx.xx.xx:xxxxx:  [len1468<asnlen8167]
02:28:02.512038 IP 63.225.235.190.snmp > xx.xx.xx.xx:xxxxx:  [P/U/U-0][!init SEQ]_02_04_09_00_00_00_30_17_06_0f_2b_06_01_02
02:28:02.595439 IP 205.171.37.238.snmp > xx.xx.xx.xx:xxxxx:  [!init SEQ]150994944
02:28:02.621187 IP 63.151.150.110.snmp > xx.xx.xx.xx:xxxxx:  [len1468<asnlen8187]
02:28:02.627391 IP 58.213.14.102.30937 > xx.xx.xx.xx:xxxxx: UDP, length 8177
02:28:02.637726 IP 58.213.14.102.30937 > xx.xx.xx.xx:xxxxx: UDP, length 8177
02:28:02.671142 IP 222.175.30.210.snmp > xx.xx.xx.xx:xxxxx:  [len1468<asnlen8183]
02:28:02.706534 IP 222.175.30.210.snmp > xx.xx.xx.xx:xxxxx:  [!init SEQ]9


Do you think my servers network should be lagging from this?
I thought maybe it could be the onboard network card (10/100/1000Mbps) that is bottlenecking, what do you think? Are there any settings to help withstand a UDP flood?

---

### Post by Ranko Kohime on 2013-05-22
I have been told that bi-directional traffic saps more than 50% of total network bandwidth, (i.e., a 100Mb full-duplex network which will reach 98Mb uni-directional, peaks out at 45Mb total bi-directional) something that my experiments have revealed to be true.  This is on large data transfers only.  I can easily see small spam packets making this situation even worse.

As for "getting through", the server still has to receive those packets to be able to log and graph them.

---

### Post by SeijiSensei on 2013-05-22
Only your ISP can keep these packets from coming into your network.  If this persists, I'd give them a call and ask them to block the sources.

---

### Post by mister3000 on 2013-05-22
> **Ranko Kohime said:**
> I have been told that bi-directional traffic saps more than 50% of total network bandwidth, (i.e., a 100Mb full-duplex network which will reach 98Mb uni-directional, peaks out at 45Mb total bi-directional) something that my experiments have revealed to be true. This is on large data transfers only. I can easily see small spam packets making this situation even worse.

So would I be able to set my server up to use 1 ethernet port for inbound data and another port for the outbound?

> **Ranko Kohime said:**
> As for "getting through", the server still has to receive those packets to be able to log and graph them.

Well they still get through, but I would suspect they should be getting through without any delay and without lagging my network. I'm just trying to find the cause of the bottleneck as I would think a 1000 Mbit port should be able to handle more than a 90 Mbit UDP flood? This makes me think it's hardware on my system bottlenecking.

> **SeijiSensei said:**
> Only your ISP can keep these packets from coming into your network. If this persists, I'd give them a call and ask them to block the sources.

I'm not really trying to block the packets. I just want my server to withstand the attack without any network lag.

---

### Post by sandyd on 2013-05-22
> **mister3000 said:**
> So would I be able to set my server up to use 1 ethernet port for inbound data and another port for the outbound?



Well they still get through, but I would suspect they should be getting through without any delay and without lagging my network. I'm just trying to find the cause of the bottleneck as I would think a 1000 Mbit port should be able to handle more than a 90 Mbit UDP flood? This makes me think it's hardware on my system bottlenecking.
[B]


I'm not really trying to block the packets. I just want my server to withstand the attack without any network lag.[/B]

Not possible without upstream filtering

For example, if you have a 100mbps line to your server.
Person sends a 100mbps (not talking about pps here even) attack to your server

Your cooked already because that 100mbps attack is filling up your line. UDP is connectionless, so your server does not even need to answer.

---

### Post by mister3000 on 2013-05-22
I understand that, which is why I'm confused. They are only sending 90 mbps and I have a 1000 mbps line.

---

### Post by Ranko Kohime on 2013-05-22
> **mister3000 said:**
> So would I be able to set my server up to use 1 ethernet port for inbound data and another port for the outbound?
Certainly.  I can't tell you how to do it, though, as I've never done it myself.  :-?

But do keep in mind that if both cards attach to the same switch, you're just moving the bottleneck up the line.

> **mister3000 said:**
> Well they still get through, but I would suspect they should be getting through without any delay and without lagging my network. I'm just trying to find the cause of the bottleneck as I would think a 1000 Mbit port should be able to handle more than a 90 Mbit UDP flood? This makes me think it's hardware on my system bottlenecking.
One would think so, but computers don't always act as we expect them too.  Are you in a position where you can do testing at the time of the attacks with another gigabit system on the same LAN?

> **mister3000 said:**
> I'm not really trying to block the packets. I just want my server to withstand the attack without any network lag.
Blocking the packets upstream may be the only way to achieve this.

---

### Post by mister3000 on 2013-05-22
> **Ranko Kohime said:**
> 
One would think so, but computers don't always act as we expect them too.  Are you in a position where you can do testing at the time of the attacks with another gigabit system on the same LAN?

No I'm not. I currently have 1 server colocated in a datacenter.

If it makes a difference I can easily download/upload at 500 Mbps (seems to be capped by the speedtest servers) but it seems if there are tons of different IP's that's when the network seems to lag.

---

### Post by sandyd on 2013-05-22
Try to increase your UDP/TCP buffers using sysctl, and see if that helps.

To check their current amount
```

# sets min/default/max TCP read buffer
sysctl net.ipv4.tcp_rmem
# sets min/pressure/max TCP write buffer
sysctl net.ipv4.tcp_wmem
# sets min/pressure/max TCP buffer space, default 31744 32256 32768
sysctl net.ipv4.tcp_mem

### CORE settings (for socket and UDP effect)
# maximum receive socket buffer size
sysctl net.core.rmem_max
# maximum send socket buffer size
sysctl net.core.wmem_max
# default receive socket buffer size
sysctl net.core.rmem_default
# default send socket buffer size
sysctl net.core.wmem_default

```

To set them (temperory) (example)
```
 sysctl -w net.core.wmem_default=xxxxxx

```

All those need root/sudo
--- Slight offtopic info ---

> For most hosts that advertise having gigabit for your server, you are sharing the gigabit line with several other servers on the same switch which is connected to a gigabit port.
Lets do some realistic calculations:

I will take QuadraNET's LAX Datacenter at 1 Wilshire as an example right now.

```

nLayer -- Transit -- 2 x 10Gbps
Tiscali / Inteliquent -- Transit -- 2 x 10Gbps
PCCW/BTN -- Transit -- 1 x 10Gbps
Equinix LAIIX -- Peering -- 1 x 10Gbps
Any2Exchange -- Peering - 1 x 10Gbps
Host.net -- Peering -- 2 x 10Gbps
HiNet Taiwan -- Peering -- 1 x 10Gbps
ChinaUnicom Direct -- Peering -- 1x 10Gbps

```

Now, add them all up (excluding [private peering]("http://www.peeringdb.com/view.php?asn=29761"))... which equals 110Gbps. If QuadraNET was using dedicated 1Gib ports (which they arent), they would only have the capacity to host 110 servers with gigabit ports, which isnt quite possible, even with overselling because people buy gigabit ports over 100mbps ports for a reason. Imagine the amount of bandwidth needed to actually support 200-300 gigabit servers.

Unless you have a dedicated gigabit port (today, most gigabit lines are shared unless otherwise stated), your gigabit port is *burstable* up to 1G/s, but is unlikely to reach full speeds unless the other servers on the switch are doing nothing.

---

### Post by mister3000 on 2013-05-22
I increased "net.core.netdev_max_backlog" and now my users packets aren't dropped but are instead delayed. Does this mean my kernel can't process the packets fast enough as they come in? If so, how could I speed packet processing up?

---

### Post by sandyd on 2013-05-23
> **mister3000 said:**
> I increased "net.core.netdev_max_backlog" and now my users packets aren't dropped but are instead delayed. Does this mean my kernel can't process the packets fast enough as they come in? If so, how could I speed packet processing up?

That setting allows you to increase the backlog - see above post for commented instructions on the variables that you need and what they do

---

