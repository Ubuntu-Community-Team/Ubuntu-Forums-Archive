---
title: "[SOLVED] Really strange Ubuntu Router/NAT problem"
date: 2008-11-12
forum: Server Platforms
---

### Post by jrutila on 2008-11-12
This is something really weird.

I have one Intrepid Ubuntu as a router/firewall and two Ubuntus (laptops) NATted behind it. From the router I can access certain webpages (ok, piratebay) fine. But when I try to connect those webpages from one of the laptops it can't connect. Connection is established (according to netstat) and it is also NATted (according to netstat-nat in router). But nothing happens.

The weird part is that most of the other pages work well (eg. google, digg frontpage, etc.).

This looks like I can connect to those pages, but incoming traffic is blocked. And why it is just some pages?

Someone please give me a hint where my problem could reside.

---

### Post by koenn on 2008-11-12
what do you mean, "nothing happens"? the pirate bay pages don't load ? the torrents don't start ? your computer hangs ?

---

### Post by prshah on 2008-11-12
> **jrutila said:**
> This is something really weird.
Someone please give me a hint where my problem could reside.

See [http://ubuntuforums.org/showpost.php?p=4514356&postcount=12](http://ubuntuforums.org/showpost.php?p=4514356&postcount=12) and [http://ubuntuforums.org/showpost.php?p=4756898&postcount=20](http://ubuntuforums.org/showpost.php?p=4756898&postcount=20) for a possible "mtu fix". For the second link, you should probably take a look at the [whole 2nd page]("http://ubuntuforums.org/showthread.php?t=760915&page=2")

---

### Post by jrutila on 2008-11-13
I slept it over and now I have narrowed the problem a little.

Forgot to mention that I have wireless LAN in my home and the traffic is tunneled with ipsec across the wireless (so secured WLAN without WEP/WPA).

And... Everything works without ipsec but when ipsec is enabled (with setkey and ipsec-tools.conf), certain web pages just load and load and load...

Changing the mtu values in network interfaces (with ipsec disabled or enabled) doesn't seem to have any change. Or I'm doing it somewhat wrong, where should I change the mtu? Now I have done just "ifconfig eth0 mtu 1492".

This is myt setup
```

Laptop (wlan0) (192.168.1.52)
|
| ipsec tunnel over WLAN (and wireless bridge)
|
Router (eth0) (192.168.1.1)
Router (eth1) (82.211.*.*)
|
Internet

```

And here is my ipsec-tools.confs

On laptop:
```

add 192.168.1.1 192.168.1.52 esp 691 -m tunnel -E 3des-cbc
        0xHIDDEN1;
add 192.168.1.52 192.168.1.1 esp 693 -m tunnel -E 3des-cbc
        0xHIDDEN2;

spdadd 192.168.1.52 0.0.0.0/0 any -P out ipsec
	esp/tunnel/192.168.1.52-192.168.1.1/require;
spdadd 0.0.0.0/0 192.168.1.52 any -P in ipsec
	esp/tunnel/192.168.1.1-192.168.1.52/require;

```

And on router:
```

add 192.168.1.1 192.168.1.52 esp 691 -m tunnel -E 3des-cbc
        0xHIDDEN1;
add 192.168.1.52 192.168.1.1 esp 693 -m tunnel -E 3des-cbc
        0xHIDDEN2;

spdadd 192.168.1.52 0.0.0.0/0 any -P in ipsec
        esp/tunnel/192.168.1.52-192.168.1.1/require;
spdadd 0.0.0.0/0 192.168.1.52 any -P out ipsec
        esp/tunnel/192.168.1.1-192.168.1.52/require;

```

Above configuration works, but some web pages just keep loading and never finish. After disabling ipsec, everything works. I will investigate this more, but any advise is good. prshah, where should I set mtu values and which interfaces (wlan0, eth0, eth1)? I think your hints were about setting some external router's mtu lower. I don't have external router (well, I have but it is just a wlan bridge to my home LAN)

Thanks for your help so far

---

### Post by iponeverything on 2008-11-13
Does wireless device on your linux router/nat box support ap mode (with wpa2) -- if it does, then just configure that and turn off ipsec since it is the source of the problem.  A lot of the madwifi drivers support ap.

---

### Post by prshah on 2008-11-13
> **jrutila said:**
> where should I change the mtu? Now I have done just "ifconfig eth0 mtu 1492".

where should I set mtu values and which interfaces (wlan0, eth0, eth1)? 


Well, it was just a suggestion..

In any case, as you've pointed out, I meant you have to change the mtu for the LAN interface on your router (not WAN). In your case, I'd guess it means you'll have to change the MTU for the network interface that your LAN uses on the intrepid router/firewall system.

Again, I don't know how valid this suggestion is, but it seems similar to the problem I had, so I threw it out there.. you can feel free to throw it out after about 5 mins of testing; I don't believe you will need more time than that.

In summary: On your Intrepid router / firewall system, set the MTU of the interface connecting to the LAN to 1492 and see it web browsing performance (instantly) improves; otherwise, I guess this is not your problem.

---

### Post by jrutila on 2008-11-13
prshah, I tried setting the MTU value for eth0 (which is the LAN interface) but had no success. I think the problem is not about that. Thanks for the hints, nevertheless.

iponeverything, thanks for suggestion. I really would like to keep my WLAN "open" so anyone can access to the Internet through it. but at the same time keep my own traffic hidden from some eavesdropper.
Do you have any suggestion why IPsec would act like this? Does it drop some high ports? Doesn't IPsec like NATting?

If it's any help, here is list of web pages that doesn't work (they work from router and from laptop without ipsec). I have two laptops and those same pages are not working from neither of them.

-piratebay.org
-torrentfreak.com
-opensubtitles.org
(ok, it starts to sound like my router is controlled by MPAA)
-any digg sub-page (those "top in all topics" -links, front page works)

Is there alternative for IPsec to secured home WLAN traffic at the same time keeping WLAN free to use by anyone?

---

### Post by koenn on 2008-11-13
> **jrutila said:**
>  Doesn't IPsec like NATting?
It doesn't : parts of the IP headers that are relevant to NAT, get encrypted
(dest and/or src address, iirc) so the translation fails.

SSL-vpn doesn't have that problem and passes through NAT effortlessly. OpenVPN is the current standard implementation, but I can't really tell if that's a solution in your case.

---

### Post by jrutila on 2008-11-19
Sorry, I've been little busy lately, but I have now some new information regarding the problem. It maybe is about the MTU after all (or something similar). Here is some tcpdump from the router's eth1 (facing the Internet) interface.

XXX is my host and 83.140.65.11 is thepiratebay.org (one of the sites I can't access)

First: without IPsec (can access)
```

root@XXX:~# tcpdump -i eth1 dst 83.140.65.11
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth1, link-type EN10MB (Ethernet), capture size 96 bytes
17:28:04.981120 IP XXX.44317 > 83.140.65.11.www: F 3084688367:3084688367(0) ack 575728862 win 137
17:28:04.981304 IP XXX.44319 > 83.140.65.11.www: S 3334420421:3334420421(0) win 5840 <mss 1460,sackOK,timestamp 21334170 0,nop,wscale 
7>
17:28:05.017150 IP XXX.44319 > 83.140.65.11.www: . ack 941154703 win 46
17:28:05.022923 IP XXX.44319 > 83.140.65.11.www: P 0:472(472) ack 1 win 46
17:28:05.070346 IP XXX.44319 > 83.140.65.11.www: . ack 1461 win 69
17:28:05.070649 IP XXX.44319 > 83.140.65.11.www: . ack 2459 win 92
17:28:05.104501 IP XXX.44319 > 83.140.65.11.www: . ack 3218 win 115
17:28:05.434661 IP XXX.44319 > 83.140.65.11.www: P 472:925(453) ack 3218 win 115
17:28:05.468874 IP XXX.44319 > 83.140.65.11.www: . ack 4265 win 137
17:28:11.032411 IP XXX.44319 > 83.140.65.11.www: . ack 4266 win 137
10 packets captured
10 packets received by filter
0 packets dropped by kernel

```

Second: with IPsec (can't access)
```

root@XXX:~# tcpdump -i eth1 dst 83.140.65.11
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth1, link-type EN10MB (Ethernet), capture size 96 bytes
17:29:33.427505 IP XXX.44321 > 83.140.65.11.www: S 420345481:420345481(0) win 5840 <mss 1460,sackOK,timestamp 21356281 0,nop,wscale 7>
17:29:33.478673 IP XXX.44321 > 83.140.65.11.www: . ack 2258717180 win 46
17:29:33.479081 IP XXX.44321 > 83.140.65.11.www: P 0:472(472) ack 1 win 46
17:29:33.553137 IP XXX > 83.140.65.11: ICMP XXX unreachable - need to frag (mtu 1462), length 556
17:29:33.558683 IP XXX.44321 > 83.140.65.11.www: . ack 1 win 46
17:29:36.552763 IP XXX > 83.140.65.11: ICMP XXX unreachable - need to frag (mtu 1462), length 556
17:29:38.612927 IP XXX.44321 > 83.140.65.11.www: . ack 1 win 46
17:29:42.552843 IP XXX > 83.140.65.11: ICMP XXX unreachable - need to frag (mtu 1462), length 556
17:29:54.552783 IP XXX > 83.140.65.11: ICMP XXX unreachable - need to frag (mtu 1462), length 556
9 packets captured
11 packets received by filter
0 packets dropped by kernel

```

I will go googling about this, but help is also welcome.

---

### Post by prshah on 2008-11-19
> **jrutila said:**
> It maybe is about the MTU after all (or something similar). 

Second: with IPsec (can't access)
```

17:29:33.553137 IP XXX > 83.140.65.11: ICMP XXX unreachable
 - need to frag [color=red](mtu 1462)[/color], length 556

```


One of the "posters" to whom I'd suggested the MTU fix (MTU 1492) had mentioned that he got better performance with 1462. Just pointing it out; I'll see if I can dig up that post / thread.

I can't really recommend anything, though; MTU related fixes are "black magic" fixes for me.

---

### Post by jrutila on 2008-11-19
prshah, changing the mtu to 1462 (ifconfig eth0 mtu 1462) resulted in following:

btw, eth0 was inner LAN
```

19:27:24.861590 IP XXX > 83.140.65.11: ICMP XXX unreachable - need to frag (mtu 1422), length 556

```

And changing mtu on eth0 to 1422 resulted in following:
```

19:31:46.890099 IP XXX > 83.140.65.11: ICMP XXX unreachable - need to frag (mtu 1382), length 556

```

and so on, resulting tcpdump message mtu always 40 smaller than mtu of interface (eth0 mtu 1382 -> need to frag (mtu 1342))

There seems to be some kind of pattern, but I have no idea how to fix this.

---

### Post by jrutila on 2009-01-05
I revisited this problem today (been driwing with open wlan until now) and suddenly got it working!

The solution was to put the mtu setting to the **clients**.
So I did on my laptop (192.168.1.52) following

```
ifconfig wlan0 mtu 1462
```

I was little dazzled, because I thought that I tried this already. Maybe this was the instruction I was told here, but I didn't catch it. Anyways, now I can access all sites.

One other thing on the router I did was to put "Clamp MSS to MTU" (I used firewall biulder). I don't know if this helped any way.

Thank you all who helped.

Extra hint:
To set the mtu automatically I edited routers /etc/dhcp3/dhcpd.conf and put ```
option interface-mtu 1462;
``` on hosts with ipsec. This way my laptop uses mtu 1462 only when I'm at my home network.

---

