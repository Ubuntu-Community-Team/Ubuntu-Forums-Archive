---
title: "Problems with nat routing on Ubuntu 18.04"
date: 2018-05-12
forum: Server Platforms
---

### Post by Irihapeti on 2018-05-12
I have a single-board computer (PC Engines APU 1D4) which I use as my home LAN router. It's been running Ubuntu 16.04 for about 18 months with no problems.

Though I'm in no rush to upgrade, I've been testing out 18.04, and I've run into problems with nat routing. Namely, I can ping from a PC through the router to an outside address, but connecting with a browser is patchy. Sometimes it connects and sometimes I get "connecting to xyz.com" (then "initiating a TLS handshake with xyz.com" if it's a https site) and there it remains stuck. Lynx fairs no better than the graphical browsers, and IRC doesn't work, either.

Traceroute reaches the remote site. Oddly enough, once I've done a traceroute, I can nearly always then connect with the browser.

Items on the LAN are no problem, but they're all on the same bridge interface.

Configurations used on 18.04 are the same as on 16.04. I thought that maybe NetPlan was a problem so I went back to ifupdown. Still no dice. Disabling dnsmasq and using static IPs on the LAN didn't help, either.

The only thing that might be considered unusual with the setup is pppoe. But as I've mentioned, 16.04 is handling it no problem.

Does anyone have any ideas?

---

### Post by CharlesA on 2018-05-13
Run tcpdump on the router itself to see if it is actually establishing the connections or not. I suppose it's possible that there are firewall rules in place to block related traffic, but I doubt that's the case if ping is working..

---

### Post by Irihapeti on 2018-05-13
Thanks for the hint. I've done that and I'll need a little while to have a close look and see if anything interesting in the logs.

The firewall rules were copied from the 16.04 install. I've made one or two tweaks to change from br0 to enp2s0 (to eliminate bridge probs) and that's all. Therefore, I doubt it's the firewall, but I know it's always possible to stare at text and not see the obvious. :)

---

### Post by SeijiSensei on 2018-05-14
Do you have the same problems if you purge the firewall rules?  If so, that eliminates one possible source.

---

### Post by Irihapeti on 2018-05-14
Same problem with either no firewall rules or with a minimal set to enable masquerade.

Here are the minimal rules I used:

```
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
iptables -A FORWARD -i enp2s0 -o ppp0 -j ACCEPT
```

Remove the second line and leaving just the masquerade entry didn't work, either.

The funny thing is, I've been playing with VMs and internal networking, and it all works there. Those are intel nics; the router has Realtek ones. Would that have anything to do with it?

BTW, Debian stretch works OK, so I do have options.

---

### Post by Irihapeti on 2018-05-14
A snippet from tcpdump, LAN port, when a webpage is refusing to load:

```

listening on enp2s0, link-type EN10MB (Ethernet), capture size 262144 bytes
19:39:39.264830 IP 192.168.1.65.47504 > 50.19.253.65.443: Flags [S], seq 1008201029, win 29200, options [mss 1460,sackOK,TS val 1555411790 ecr 0,nop,wscale 7], length 0
19:39:39.474420 IP 50.19.253.65.443 > 192.168.1.65.47504: Flags [S.], seq 3766295431, ack 1008201030, win 26847, options [mss 1460,sackOK,TS val 350713429 ecr 1555411790,nop,wscale 7], length 0
19:39:39.474612 IP 192.168.1.65.47504 > 50.19.253.65.443: Flags [.], ack 1, win 229, options [nop,nop,TS val 1555412000 ecr 350713429], length 0
19:39:39.478073 IP 192.168.1.65.47504 > 50.19.253.65.443: Flags [P.], seq 1:518, ack 1, win 229, options [nop,nop,TS val 1555412003 ecr 350713429], length 517
19:39:39.692048 IP 50.19.253.65.443 > 192.168.1.65.47504: Flags [.], ack 518, win 219, options [nop,nop,TS val 350713646 ecr 1555412003], length 0
19:39:39.695988 IP 50.19.253.65.443 > 192.168.1.65.47504: Flags [P.], seq 2897:3091, ack 518, win 219, options [nop,nop,TS val 350713648 ecr 1555412003], length 194
19:39:39.696299 IP 192.168.1.65.47504 > 50.19.253.65.443: Flags [.], ack 1, win 237, options [nop,nop,TS val 1555412222 ecr 350713646,nop,nop,sack 1 {2897:3091}], length 0
19:39:44.538092 ARP, Request who-has 192.168.1.65 tell 192.168.1.1, length 28
19:39:44.538248 ARP, Reply 192.168.1.65 is-at yyyyyyyyyyyy, length 46
19:39:49.696592 IP 192.168.1.65.47504 > 50.19.253.65.443: Flags [.], ack 1, win 237, options [nop,nop,TS val 1555422222 ecr 350713646,nop,nop,sack 1 {2897:3091}], length 0
19:39:49.907592 IP 50.19.253.65.443 > 192.168.1.65.47504: Flags [.], ack 518, win 219, options [nop,nop,TS val 350723861 ecr 1555412222], length 0
19:40:00.160117 IP 192.168.1.65.47504 > 50.19.253.65.443: Flags [.], ack 1, win 237, options [nop,nop,TS val 1555432686 ecr 350713646,nop,nop,sack 1 {2897:3091}], length 0
19:40:00.369121 IP 50.19.253.65.443 > 192.168.1.65.47504: Flags [.], ack 518, win 219, options [nop,nop,TS val 350734325 ecr 1555412222], length 0
19:40:10.399641 IP 192.168.1.65.47504 > 50.19.253.65.443: Flags [.], ack 1, win 237, options [nop,nop,TS val 1555442926 ecr 350713646,nop,nop,sack 1 {2897:3091}], length 0
19:40:10.608516 IP 50.19.253.65.443 > 192.168.1.65.47504: Flags [.], ack 518, win 219, options [nop,nop,TS val 350744565 ecr 1555412222], length 0
19:40:20.639131 IP 192.168.1.65.47504 > 50.19.253.65.443: Flags [.], ack 1, win 237, options [nop,nop,TS val 1555453166 ecr 350713646,nop,nop,sack 1 {2897:3091}], length 0
19:40:20.847659 IP 50.19.253.65.443 > 192.168.1.65.47504: Flags [.], ack 518, win 219, options [nop,nop,TS val 350754804 ecr 1555412222], length 0
19:40:25.758888 ARP, Request who-has 192.168.1.1 tell 192.168.1.65, length 46
19:40:25.758980 ARP, Reply 192.168.1.1 is-at xxxxxxxxxxxx, length 28
19:40:30.878492 IP 192.168.1.65.47504 > 50.19.253.65.443: Flags [.], ack 1, win 237, options [nop,nop,TS val 1555463406 ecr 350713646,nop,nop,sack 1 {2897:3091}], length 0
19:40:31.093695 IP 50.19.253.65.443 > 192.168.1.65.47504: Flags [.], ack 518, win 219, options [nop,nop,TS val 350765044 ecr 1555412222], length 0
19:40:36.250101 ARP, Request who-has 192.168.1.65 tell 192.168.1.1, length 28
19:40:36.250264 ARP, Reply 192.168.1.65 is-at yyyyyyyyyyyy, length 46
19:40:41.118145 IP 192.168.1.65.47504 > 50.19.253.65.443: Flags [.], ack 1, win 237, options [nop,nop,TS val 1555473646 ecr 350713646,nop,nop,sack 1 {2897:3091}], length 0
19:40:41.327151 IP 50.19.253.65.443 > 192.168.1.65.47504: Flags [.], ack 518, win 219, options [nop,nop,TS val 350775284 ecr 1555412222], length 0
19:41:47.365183 IP 192.168.1.65.5353 > 224.0.0.251.5353: 0 [3q] PTR (QM)? _ipps._tcp.local. PTR (QM)? _nmea-0183._tcp.local. PTR (QM)? _ipp._tcp.local. (62)
19:42:43.975925 IP 192.168.1.65.47504 > 50.19.253.65.443: Flags [F.], seq 518, ack 1, win 237, options [nop,nop,TS val 1555596510 ecr 350713646,nop,nop,sack 1 {2897:3091}], length 0
19:42:44.186108 IP 50.19.253.65.443 > 192.168.1.65.47504: Flags [F.], seq 3091, ack 519, win 219, options [nop,nop,TS val 350898147 ecr 1555596510], length 0
19:42:44.186229 IP 192.168.1.65.47504 > 50.19.253.65.443: Flags [R], seq 1008201548, win 0, length 0
19:42:49.111561 ARP, Request who-has 192.168.1.1 tell 192.168.1.65, length 46
19:42:49.111655 ARP, Reply 192.168.1.1 is-at xxxxxxxxxxxx, length 28
19:42:49.370101 ARP, Request who-has 192.168.1.65 tell 192.168.1.1, length 28
19:42:49.370250 ARP, Reply 192.168.1.65 is-at yyyyyyyyyyyy, length 46

```

---

### Post by SeijiSensei on 2018-05-14
Have you tried connecting to the site by IP address ([https://10.10.10.10/](https://10.10.10.10/)) rather than domain name?  Let's rule out DNS resolution problems while we're at it.

---

### Post by Irihapeti on 2018-05-14
Unfortunately, it doesn't make any difference. It still gets stuck on "Performing a TLS handshake to $IP"

---

### Post by Irihapeti on 2018-05-18
I did another experiment today with nat routing. I connected the PC to the ethernet port of my laptop, as follows:

```

           ppp0
    +-------|-------+
    |               |
    |               |
    |  192.168.1.1  | <- original router (running 16.04)
    |               |
    |               |
    |               |
    +-------|-------+
            |
          wlan
            |
    +-------|-------+                 +---------------+ 
    |  192.168.1.x  |                 |               |
    |               |                 |      (PC)     |
    |   (laptop)    |                 |  192.168.4.2  |
    |               |                 |               |
    |               |     enp3s0      |               |
    |  192.168.4.1  -------------------               |
    +---------------+                 +---------------+


```
The laptop was running a command-line version of 18.04. Two lines of iptables to set up forwarding/masquerade. Static IP addresses on laptop and PC. nameserver set manually in PC.

It worked. It was a little slow at times, but it worked.

The laptop has Atheros wireless and also Atheros (Attansic, actually) ethernet. It's an old EeePC900.

I'm more seriously wondering if the Realtek nics on the router have something to do with it, combined with the 4.15 kernel.

I shall keep looking. If I'm right, sooner or later someone else has to report something similar.

---

### Post by Irihapeti on 2018-05-26
I know that it's not usually recommended, but this was one instance where a reinstall (of 18.04) really did solve the problem. I have no idea what exactly was wrong, but it's working now.

---

### Post by reinhard.munz on 2018-08-01
You wondered whether anyone else has the same problem. I have the exact same problem with my Debian router. Upgraded from Jessie to Stretch few days ago and have seen an increasing number of clients complaining about connection issues. I switched back to Jessie today and the problems are gone.

I'd prefer not to reinstall the machine. So in case anyone reading this knows what the problem is, I'm all ears.

Just in case, some more details
It's not only TLS connections, I've seen few non-encrypted connections that consistently did not work.
It's not all the TLS connections. However, behavior was consistent. So connections that worked always worked and those that didn't work never worked (as far as my testing went).

Thanks btw for the hint with the NICs. I'll see what I can do about that. Unfortunately this router runs on top of Citrix XenServer and I'm not sure whether I can change the hardware the VM sees. I'll see whether there is any change after the next update cycle of the servers.

---

