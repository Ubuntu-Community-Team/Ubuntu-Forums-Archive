---
title: "[SOLVED] Strange packets to 64.125.152.160.available.above.net"
date: 2007-11-24
forum: Server Platforms
---

### Post by PetePete on 2007-11-24
decided to launch tcpdump to see what was happening on my server, not suspicious of anything, just interested. I notice frequent entries like the ones below

```

15:56:34.248831 IP 64.125.152.160.available.above.net.34783 > 192.168.2.11.32181: S 936151803:936151803(0) win 5840 <mss 1460,sackOK,timestamp 2735876821 0,nop,wscale 2>
15:56:34.249035 IP 192.168.2.11.32181 > 64.125.152.160.available.above.net.34783: R 0:0(0) ack 936151804 win 0
15:56:37.249049 IP 64.125.152.160.available.above.net.34783 > 192.168.2.11.32181: S 936151803:936151803(0) win 5840 <mss 1460,sackOK,timestamp 2735879821 0,nop,wscale 2>
15:56:37.249143 IP 192.168.2.11.32181 > 64.125.152.160.available.above.net.34783: R 0:0(0) ack 1 win 0
15:56:43.247544 IP 64.125.152.160.available.above.net.34783 > 192.168.2.11.32181: S 936151803:936151803(0) win 5840 <mss 1460,sackOK,timestamp 2735885821 0,nop,wscale 2>
15:56:43.247643 IP 192.168.2.11.32181 > 64.125.152.160.available.above.net.34783: R 0:0(0) ack 1 win 0
15:56:55.245721 IP 64.125.152.160.available.above.net.34783 > 192.168.2.11.32181: S 936151803:936151803(0) win 5840 <mss 1460,sackOK,timestamp 2735897821 0,nop,wscale 2>
15:56:55.245829 IP 192.168.2.11.32181 > 64.125.152.160.available.above.net.34783: R 0:0(0) ack 1 win 0
15:57:19.241584 IP 64.125.152.160.available.above.net.34783 > 192.168.2.11.32181: S 936151803:936151803(0) win 5840 <mss 1460,sackOK,timestamp 2735921821 0,nop,wscale 2>


```

cant think why my server is connecting to *.above.net

any ideas anyone?! 
going to monitor it for a little longer then prob drop the packets to that subnet.

---

### Post by MJN on 2007-11-24
See what process is listening (and responding) on port 32181 with:

```
sudo lsof -i :32181
```

That may shed some light on it...

Mathew

---

### Post by PetePete on 2007-11-24
there is no process listening, the ports not even open, just done a full port scan and no ports are open (except known services ive setup)

---

### Post by MJN on 2007-11-24
Is tcpdump still showing the packets? Something *was* listening on that port given it was responding as shown in the trace.

Were there any network-enabled applications running at the time of these packets appearing?

Mathew

---

### Post by PetePete on 2007-11-24
yes tcpdump is still showing them, although i have set iptables to drop the packets now, so nothing is responding.
the computer is a server, but no applications were running that take connections except the ssh i was using to remotly login.

still getting them, and also changing ports and sometimes a different IP
```

18:37:26.569890 IP 64.125.152.188.available.above.net.45719 > 192.168.2.11.32181: S 2038880958:2038880958(0) win 5840 <mss 1460,sackOK,timestamp 3352843815 0,nop,wscale 2>
18:37:41.633241 IP 64.125.154.36.available.above.net.47276 > 192.168.2.11.32181: S 3769801362:3769801362(0) win 5840 <mss 1460,sackOK,timestamp 3690442051 0,nop,wscale 2>
18:37:54.938577 IP BelkinModem.Belkin > ALL-SYSTEMS.MCAST.NET: igmp query v2
18:39:41.222090 IP 64.125.152.160.available.above.net.58500 > 192.168.2.11.32181: S 2686146673:2686146673(0) win 5840 <mss 1460,sackOK,timestamp 2745665538 0,nop,wscale 2>
18:39:50.220550 IP 64.125.152.160.available.above.net.58500 > 192.168.2.11.32181: S 2686146673:2686146673(0) win 5840 <mss 1460,sackOK,timestamp 2745674538 0,nop,wscale 2>

```

---

### Post by MJN on 2007-11-24
That's different now - your server process is not responding to them. Or is this with iptables dropping them? (I'd leave them coming through as you need to find your server process that was responding before)

Are you sure you weren't running some thing like a torrent application, or other P2P app, before? The continuation of these packets now would be entirely consistent with this as the other peer still tries to see if you're still there.

Leave iptables out of it and see if you've got a process responding to the packets - lsof will show you what it is.

Mathew

---

### Post by PetePete on 2007-11-24
ok i will remove the rules i put into iptables..
there is no p2p apps on the computer, the only things that should communicate with outside world is dynamic dns to update itself, and im sure these packets aren't anything to do with that.

the computer is quite simple, running ubuntu server edition, no gui, just squid + ssh, used for remote storage/secure browsing when using unsecure wireless hotspots etc. .. so no  fancy apps which could be doing stuff.

---

### Post by PetePete on 2007-11-24
thanks for the help, much appreciated but how do i use lsof to find the process?
ran the following.. (removedIPAddress = my own IP)

```

pete@linux-server:~$ sudo lsof | grep TCP
sshd       3295   root    3u     IPv6       7299                TCP *:ssh (LISTEN)
squid     11352  proxy   13u     IPv4      45839                TCP *:3128 (LISTEN)
sshd      19715   root    3u     IPv6      77564                TCP 192.168.2.11:ssh->removedIPAddress:61148 (ESTABLISHED)
sshd      19717   pete    3u     IPv6      77564                TCP192.168.2.11:ssh->removedIPAddress:61148 (ESTABLISHED)
sshd      19809   root    3u     IPv6      78082                TCP 192.168.2.11:ssh->removedIPAddress:61669 (ESTABLISHED)
sshd      19811   pete    3u     IPv6      78082                TCP 192.168.2.11:ssh->removedIPAddress:61669 (ESTABLISHED)

```

ps..
the server is behind a router/firewall with only port forwarding enabled for the ssh (which has been set to non-default port)

---

### Post by killerdragon on 2007-11-24
I'm going out on a limb here and saying that its a worm or trojan trying to get in.

Here is some insight on port 58500:
[https://www.securetrust.com/resources/portsearch/port/58500/58999/](https://www.securetrust.com/resources/portsearch/port/58500/58999/)

Just my guess.

I would tell iptables to drop all packets from the IP address range that was given to above.net.
Would you be located in New York by any chance?
[http://www.dnsstuff.com/tools/whois.ch?ip=64.125.152.160](http://www.dnsstuff.com/tools/whois.ch?ip=64.125.152.160)

---

### Post by PetePete on 2007-11-24
hmm but how does it even get to my computer, its behind a router/firewall that should stop all the background traffic.

live in UK atm.

---

### Post by MJN on 2007-11-24
It's not traffic *trying* to get in - it's in and having a conversation with a process on port 32181 as demonstrated by the original tcpdump output.

You need to monitor tcpdump for outgoing packets (e.g. 
those such as *15:56:34.249035 IP 192.168.2.11.32181 > 64.125.152.160.available.above.net.34783: ....*) and then check what process is using that source port with **sudo lsof -i :32181**).

With regards to port forwarding, or rather the lack of explicit forwarding rules for these ports, is explained by the fact that your router will automatically the ports established _by an outgoing connection_. Hence, if a client process of yours on port 32181 initiated the connection to the remote machine 64.125.152.160 on port 34783 then your router automatically sets up a n incoming port forwarding rule for port 32181 to go to your machine - it becomes part of the NAT state table and persists for as long as the router thinks the connection is alive (this varies between routers and in some cases can be kept alive merely by the remote computer sending packets without any response from your client).

Mathew

P.S. Be very careful jumping to any conclusions about high numbered ports and what's using them as by their very nature they are for use as an ephemeral port by any client process purely at random so just because a client picks a port that is often used by some dodgy worm doesn't mean that said client process is that worm...

---

### Post by PetePete on 2007-11-25
sudo lsof -i :32181 doesn't come up with anything, ive tried it just after the packets have been sent/received, and also ran at the same time (just as the request came in)

looking on google the IPs from available.above.net seem to be routers, i was wondering maybe its some router which my data is passing through as I remotely ssh over the internet? like a keep alive packet or something... dunno much about this sort of thing!

I highly doubt my server has been compromised as there is only 1 user (myself), with a strong password and only service been ssh on a non-default port + fail2ban running, and only software installed from reps. also regularly update and also use tripwire to monitor any suspicious file changes which there haven't been. Although saying this, next time i am physically near the computer i think I'll wipe it and install gutsy server just to be on safe side.

---

### Post by MJN on 2007-11-25
Can you post a new tcpdump trace (showing the two-way traffic) with the associated lsof output at the same time?

I wouldn't go as far as reinstalling the OS - afterall if you're doing that out of suspicion of something untoward then you really ought to investigate how the situation came about to stop it happening again.

Mathew

---

### Post by PetePete on 2007-11-25
there is also other strange packets floating around (UDP) but the ip addresses seem to come up once, then never re-appear, unlike the *.available.above.net which sends requests every minute or so.

here is the outputs, ran this as soon as i saw the incoming request
```


pete@linux-server:~$ sudo lsof -i
COMMAND   PID USER   FD   TYPE DEVICE SIZE NODE NAME
sshd     3295 root    3u  IPv6   7299       TCP *:ssh (LISTEN)
sshd    21416 root    3u  IPv6  82616       TCP 192.168.2.11:ssh->myIPAddress:61401 (ESTABLISHED)
sshd    21418 pete    3u  IPv6  82616       TCP 192.168.2.11:ssh->myIPAddress:61401 (ESTABLISHED)
sshd    21569 root    3u  IPv6  84428       TCP 192.168.2.11:ssh->myIPAddress:61948 (ESTABLISHED)
sshd    21571 pete    3u  IPv6  84428       TCP 192.168.2.11:ssh->myIPAddress:61948 (ESTABLISHED)

```

heres an extended output of tcpdump, ran with command "sudo tcpdump -p -i eth0 -F filter" and the filter only filters out my external IP address which im using to ssh into
```

17:30:25.949184 IP 64.125.152.188.available.above.net.33058 > 192.168.2.11.32181: S 2979637358:2979637358(0) win 5840 <mss 1460,sackOK,timestamp 3435088900 0,nop,wscale 2>
17:30:30.148354 IP 64.125.152.160.available.above.net.58102 > 192.168.2.11.32181: S 3611379679:3611379679(0) win 5840 <mss 1460,sackOK,timestamp 2827929156 0,nop,wscale 2>
17:30:42.146563 IP 64.125.152.160.available.above.net.58102 > 192.168.2.11.32181: S 3611379679:3611379679(0) win 5840 <mss 1460,sackOK,timestamp 2827941156 0,nop,wscale 2>
17:30:47.211030 IP 204.140.208.222.broad.zg.sc.dynamic.163data.com.cn.25297 > 192.168.2.11.61112: UDP, length 98
17:30:47.211245 IP 192.168.2.11 > 204.140.208.222.broad.zg.sc.dynamic.163data.com.cn: ICMP 192.168.2.11 udp port 61112 unreachable, length 134
17:30:48.862198 IP truncated-ip - 61 bytes missing! CPE0015e9d45937-CM0011ae8dde84.cpe.net.cable.rogers.com.15144 > 192.168.2.11.61112: UDP, length 101
17:30:52.645016 IP BAA930f.baa.pppool.de.64125 > 192.168.2.11.61112: UDP, length 101
17:30:52.645153 IP 192.168.2.11 > BAA930f.baa.pppool.de: ICMP 192.168.2.11 udp port 61112 unreachable, length 137
17:31:01.934436 IP 123-204-0-234.dynamic.seed.net.tw.10996 > 192.168.2.11.61112: UDP, length 98
17:31:01.934591 IP 192.168.2.11 > 123-204-0-234.dynamic.seed.net.tw: ICMP 192.168.2.11 udp port 61112 unreachable, length 134
17:31:06.143439 IP 64.125.152.160.available.above.net.58102 > 192.168.2.11.32181: S 3611379679:3611379679(0) win 5840 <mss 1460,sackOK,timestamp 2827965156 0,nop,wscale 2>
17:31:10.559156 IP cm218-254-92-3.hkcable.com.hk.26853 > 192.168.2.11.61112: UDP, length 98
17:31:10.559334 IP 192.168.2.11 > cm218-254-92-3.hkcable.com.hk: ICMP 192.168.2.11 udp port 61112 unreachable, length 134
17:31:16.848897 IP 116.138.rev.vline.pl.17843 > 192.168.2.11.61112: UDP, length 98
17:31:16.849089 IP 192.168.2.11 > 116.138.rev.vline.pl: ICMP 192.168.2.11 udp port 61112 unreachable, length 134
17:31:18.066979 IP catv.spray.net.pl.27624 > 192.168.2.11.61112: UDP, length 98
17:31:18.067101 IP 192.168.2.11 > catv.spray.net.pl: ICMP 192.168.2.11 udp port 61112 unreachable, length 134
17:31:54.133626 IP 64.125.152.160.available.above.net.58102 > 192.168.2.11.32181: S 3611379679:3611379679(0) win 5840 <mss 1460,sackOK,timestamp 2828013156 0,nop,wscale 2>
17:31:54.133818 IP 192.168.2.11.32181 > 64.125.152.160.available.above.net.58102: R 0:0(0) ack 3611379680 win 0
17:31:56.343209 IP 85.155.10.138.dyn.user.ono.com.7957 > 192.168.2.11.61112: UDP, length 98
17:31:56.343362 IP 192.168.2.11 > 85.155.10.138.dyn.user.ono.com: ICMP 192.168.2.11 udp port 61112 unreachable, length 134
17:31:58.967463 IP CPE001676af75c4-CM0014e88edcac.cpe.net.cable.rogers.com.10458 > 192.168.2.11.61112: UDP, length 98
17:31:58.967598 IP 192.168.2.11 > CPE001676af75c4-CM0014e88edcac.cpe.net.cable.rogers.com: ICMP 192.168.2.11 udp port 61112 unreachable, length 134
17:32:01.298208 IP 203-70-217-184.adsl.dynamic.seed.net.tw.26209 > 192.168.2.11.61112: UDP, length 101
17:32:01.298346 IP 192.168.2.11 > 203-70-217-184.adsl.dynamic.seed.net.tw: ICMP 192.168.2.11 udp port 61112 unreachable, length 137
17:32:12.719618 IP 122-122-83-138.dynamic.hinet.net.18641 > 192.168.2.11.61112: UDP, length 98
17:32:12.719771 IP 192.168.2.11 > 122-122-83-138.dynamic.hinet.net: ICMP 192.168.2.11 udp port 61112 unreachable, length 134
17:32:15.989097 IP 85-31-233-67.marsoft.net.23539 > 192.168.2.11.61112: UDP, length 101
17:32:15.989258 IP 192.168.2.11 > 85-31-233-67.marsoft.net: ICMP 192.168.2.11 udp port 61112 unreachable, length 137
17:32:27.393789 IP 122.89.80.42.14036 > 192.168.2.11.61112: UDP, length 98
17:32:27.393961 IP 192.168.2.11 > 122.89.80.42: ICMP 192.168.2.11 udp port 61112 unreachable, length 134
17:32:40.976780 IP 59.63.109.150.30413 > 192.168.2.11.1026: UDP, length 348
17:32:40.977006 IP 192.168.2.11 > 59.63.109.150: ICMP 192.168.2.11 udp port 1026 unreachable, length 384
17:32:47.255387 IP 64.125.152.188.available.above.net.57645 > 192.168.2.11.32181: S 3379463558:3379463558(0) win 5840 <mss 1460,sackOK,timestamp 3435378997 0,nop,wscale 2>
17:32:47.255548 IP 192.168.2.11.32181 > 64.125.152.188.available.above.net.57645: R 0:0(0) ack 3379463559 win 0
17:32:47.772018 IP 218.11.208.244.24962 > 192.168.2.11.61112: UDP, length 98
17:32:47.772127 IP 192.168.2.11 > 218.11.208.244: ICMP 192.168.2.11 udp port 61112 unreachable, length 134
17:32:50.255301 IP 64.125.152.188.available.above.net.57645 > 192.168.2.11.32181: S 3379463558:3379463558(0) win 5840 <mss 1460,sackOK,timestamp 3435381997 0,nop,wscale 2>
17:32:50.255358 IP 192.168.2.11.32181 > 64.125.152.188.available.above.net.57645: R 0:0(0) ack 1 win 0
17:32:56.253316 IP 64.125.152.188.available.above.net.57645 > 192.168.2.11.32181: S 3379463558:3379463558(0) win 5840 <mss 1460,sackOK,timestamp 3435387997 0,nop,wscale 2>
17:32:56.253397 IP 192.168.2.11.32181 > 64.125.152.188.available.above.net.57645: R 0:0(0) ack 1 win 0
17:33:01.514564 IP 89.123.219.215.24557 > 192.168.2.11.61112: UDP, length 101
17:33:01.514736 IP 192.168.2.11 > 89.123.219.215: ICMP 192.168.2.11 udp port 61112 unreachable, length 137
17:33:08.251716 IP 64.125.152.188.available.above.net.57645 > 192.168.2.11.32181: S 3379463558:3379463558(0) win 5840 <mss 1460,sackOK,timestamp 3435399997 0,nop,wscale 2>
17:33:08.251841 IP 192.168.2.11.32181 > 64.125.152.188.available.above.net.57645: R 0:0(0) ack 1 win 0
17:33:32.247596 IP 64.125.152.188.available.above.net.57645 > 192.168.2.11.32181: S 3379463558:3379463558(0) win 5840 <mss 1460,sackOK,timestamp 3435423997 0,nop,wscale 2>
17:33:32.247707 IP 192.168.2.11.32181 > 64.125.152.188.available.above.net.57645: R 0:0(0) ack 1 win 0
17:34:20.238857 IP 64.125.152.188.available.above.net.57645 > 192.168.2.11.32181: S 3379463558:3379463558(0) win 5840 <mss 1460,sackOK,timestamp 3435471997 0,nop,wscale 2>
17:34:20.238979 IP 192.168.2.11.32181 > 64.125.152.188.available.above.net.57645: R 0:0(0) ack 1 win 0
17:34:39.892066 IP S010600b0d09c8e3e.cg.shawcable.net.27090 > 192.168.2.11.1026: UDP, length 484
17:34:39.894145 IP S010600b0d09c8e3e.cg.shawcable.net.27090 > 192.168.2.11.1027: UDP, length 484
17:34:39.913171 IP S010600b0d09c8e3e.cg.shawcable.net.27090 > 192.168.2.11.1028: UDP, length 484

```

---

### Post by MJN on 2007-11-25
The real lines of interest are those originating from your IP - and in that trace (with this higher level of detail) they are all 'UDP port unreachable' messages to the remote end. This is simply your machine telling them there is nothing on port x at this end. However, your original trace shows there *was* something. Are you *sure* there are no other client services on your server?

You mentioned you are on a dynamic IP hence it could well be that the previous 'owner' of your IP had a P2P application running and all this traffic is remote clients requesting a connection to what they think is a still-existant P2P client.

Do you know when your IP changed last? The traffic ought to tail off as the remote clients get the message that their peer is no longer available however depending on the client the time this will take could vary.

I'm curious you mentioned a router/firewall - you should configure that to not forward unknown ports to your server as they serve no purpose (and indeed you're better off rejecting them at the gateway for security and performance reasons).

Mathew

P.S. The last three lines of the trace are interesting - this is indicative of so-called Messenger Spam - remote hosts looking for MS Messenger on your machine to post spam (in the form of popups). These packets should never be reaching your server hence you really do need to look at how your router/firewall is configured. Note that the source IPs of these packets will almost certainly be spoofed (and hence not the true origin).

---

### Post by PetePete on 2007-11-25
no idea how the packets are reaching my machine, the firewall is only the one which comes built into the belkin wireless routers (think this one is 3 years old or so now). checked its settings and firewall is switched on, and only should forward data to server on ssh. DMZ is disabled.

im sure that sshd is the only service running (unless its hidden). heres an output of ps -A
(although squid is also running atm, but i had switched this off to eliminate before)

```

pete@linux-server:~$ sudo ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   25 ?        00:00:00 kseriod
   70 ?        00:00:00 pdflush
   71 ?        00:00:00 pdflush
   72 ?        00:00:11 kswapd0
   73 ?        00:00:00 aio/0
 1584 ?        00:00:00 khubd
 1641 ?        00:00:25 kjournald
 1707 ?        00:00:00 logd
 1793 ?        00:00:01 udevd
 2555 ?        00:00:00 kpsmoused
 2572 ?        00:00:00 shpchpd
 2577 ?        00:00:00 pccardd
 2759 ?        00:00:00 kgameportd
 3195 tty1     00:00:00 getty
 3196 tty2     00:00:00 getty
 3197 tty3     00:00:00 getty
 3198 tty4     00:00:00 getty
 3199 tty5     00:00:00 getty
 3200 tty6     00:00:00 getty
 3245 ?        00:00:00 dd
 3247 ?        00:00:00 klogd
 3295 ?        00:00:00 sshd
 3351 ?        00:00:00 atd
 3362 ?        00:00:00 cron
21082 ?        00:00:00 fail2ban
21293 ?        00:00:00 syslogd
21496 ?        00:00:00 no-ip
21635 ?        00:00:00 sshd
21637 ?        00:00:00 sshd
21638 pts/0    00:00:00 bash
21667 ?        00:00:00 squid
21669 ?        00:00:00 squid
21672 ?        00:00:00 unlinkd
21677 pts/0    00:00:00 ps

```

last time my ip address changed was 21st Nov.

---

### Post by MJN on 2007-11-25
Your router/firewall is not doing its job - pure and simple. It sounds like you've checked the correct config so it's either a) broken, or b) badly designed. Either way it's not doing what it ought to. Blocking arbitrary packets in the router is trivial to achieve - indeed it needs effort to do otherwise given the NATing that's going on.

I have no experience of Belkin routers so cannot comment and what you should be checking. Perhaps posting the model number might enable someone to suggest further investigative actions.

ps is not a good way of finding network processes as it doesn't indicate which are bound to sockets. Stick with lsof -i as you have been (although the ps output looks entirely reasonable).

Mathew

---

### Post by PetePete on 2007-11-25
cheers for all the help, i'll have a look and see if theres upgradable firmware for the router.

---

### Post by PetePete on 2007-12-16
finally had physical access to server/network...

realised that all pcs behind the router/firewall were receiving udp packets, upgraded the router firmware and all is well now. (was a belkin F5D7632 series router)

anyway thought i'd give the final resolution to this issue just incase someone stumbles accross this thread and needs the help!

---

