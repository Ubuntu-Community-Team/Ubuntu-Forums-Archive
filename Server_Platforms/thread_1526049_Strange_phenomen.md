---
title: "Strange phenomen"
date: 2010-07-07
forum: Server Platforms
---

### Post by master-m on 2010-07-07
Hi there,

this is the last chance to calm down my wife! ;)

I have a home network which is build like this:

[LIST]
[*]1 Ubuntu 10.04 PC with gigabit network card
[*]1 Win 7 Home Edition PC with gigabit network card
[*]1 router 2 Gigabit interfaces
[*]Router (Atom CPU @1.60GHz) connected to DSL Modem
[*]Router connected to Netgear Gigabit Switch
[*]Both PCs connected to Netgear Gigabit Switch
[*]OS on the router: Ubuntu Server 9.10 (Upgrade from 9.04)
[/LIST]
Now everything works well, except  one thing.
My wife is playing a **free** mmorpg.
If I start transmission (to share the newest (k)ubuntu isos), the game starts to get awfully slow and tends to disconnect (I will call this "lags". Or is there a scientific expression?). 
Things I already did and tested:

[LIST=1]
[*]I connected the Win machine  directly to the modem, during the lagging > lags disappeared
[*]I didn't started the transmission for 1 week or more > no lags ever
[*]I started the transmission in the morning on a weekend > in the evening she complained about lags
[*]Optimized the network interfaces on the linux machines for gigabit
[LIST=1]
[*]# increase TCP max buffer size set-able using setsockopt()
net.core.rmem_max = 16777216
net.core.wmem_max = 16777216
# additionally increase number of incoming packets, default = 1000
net.core.netdev_max_backlog = 8000
# number of incoming connections, default = 128
net.core.somaxconn = 512
# increase Linux autotuning TCP buffer limits
# min, default, and max number of bytes to use
# set max to at least 4MB, or higher if you use very high BDP paths
net.ipv4.tcp_rmem = 4096 87380 16777216 
net.ipv4.tcp_wmem = 4096 65536 16777216
> no effect, I changed these after the lags appeared long ago
[/LIST]
 
[*]I optimized my iptable rules > no effect
[LIST=1]
[*]I did something like this, but I don't know, if this would have an effect: ```
iptables -t nat -A PREROUTING -i ${WAN} -s gameserver-ip -j DNAT --to-destination ${schatz}
``` To directly send packages to the Win PC
[*]I set TOS and DSCP on the INPUT chain
[*]Removed unnecessary logging events
[/LIST]
 
[*]Starting the transmission > game lags > stop transmission > still lags > reboot win > no lags
[*]Starting transmission > game lags > restart game > still lags
[*]Starting transmission > game lags > restart win network interface (deactivate/activate) > still lags
[*]Starting transmission > game lags > downloading ubuntu iso with 3.7 MB/sec on the Kubuntu PC
[*]Starting transmission > game lags > anything but the game on the Win PC works well
[*]Bought new network hardware (gigbit switch, cabel and cards everything from netgear) > No effect on the game, but local ftp is better now! :p
[*]Set the global peer limit to 60 > no effect
[/LIST]
The ip of the game server never appeared in the firewall log.
I already figured to not ignore bogus ICMP errors, as this directly affects the game (somehow). But ignoring icmp echo broadcast and all didn't affect it.
I also took into account that the ISP could block torrent, but the torrent down/up rate isn't changing during the lags of the game. In addition I use encrypted connections only.
And I only upload with 10K/s and download with 200K/s

I found out that the lags mostly appear during a time, a lot of people are playing the game and the servers are nearly full (status message of the games servers).
Some people of the game said, that during this time, the game produces more traffic.

Our internet connection should have 32 Mbit down and 2 MBit up.
Speed tests (without transmission in the background) show 29 and 1.2 MBit/s.

I think this is all I tested until now. If I forgot some information, please feel free to ask.
Any hint would be appreciated.


bye,
me

---

### Post by arrrghhh on 2010-07-07
I have a 16mb internet connection.  I believe they give me 5mb up... I have to cap my upload bandwidth or else things like this happens.

I see you said you cap your upload to 10kbps.  That's... incredibly low.  So perhaps my idea just went out the window.

How is web browsing for you?  I was having issues playing games online or browsing the web until I capped my upload bandwidth to 200kbps.  Perhaps it's not being capped properly, I would use the router to see how much WAN bandwidth you are truly consuming when you're having the issues.  My bet would be it's over-utilizing the internet circuit.

---

### Post by master-m on 2010-07-07
The 200/10kbps (down/up) limit is during daytime. After midnight I once used an alternative up/down rate. But now I use the alternative speed to set the bandwidth to 0 during the daytime. 
I forgot to mention, that the lags also occur, if the transmission is running with 0 up and down. Just tested this one.

Browsing and everything else is working really good. I always did Kubuntu updates with nearly 2 MBit/s with the transmission running on the router.

<ignore-this>How can I check the bandwidth with my router? Some kind of tool for this out there?</ignore-this>
Okay, found "bmon", looks good.
But I forgot, I have gkrellmd running on the router and this shows the bandwidth. 
It never goes above 30K without transmission. Most of the time it is below 10K.
With transmission running at 0 up/down gkrellm shows nearly nothing and the game lags.

Still it is very strange, as the game is the only thing affected.
I also moved the port of transmission far away from the ports the game is using.
I found the ports and ip of the game with a Win firewall, as this complains about new connections.

---

### Post by arrrghhh on 2010-07-07
Hrm... I would venture to bet it's something different.

To truly get traffic at the router, you'd need a router that's capable of showing those types of stats.  Highly depends on what router you have, I use a Linksys router - DD-WRT enables me to monitor bandwidth, the stock Linksys firmware wouldn't show it.

---

### Post by master-m on 2010-07-07
The router is a PC with Intel Atom Cpu, 2 GB Ram, headless with OS Ubuntu Server 9.10.
The router pc is connected to a thomson dsl modem.

---

### Post by arrrghhh on 2010-07-07
Oh!  Well, that changes things.  You should definitely be able to get some pretty good WAN stats from that thing!

---

### Post by master-m on 2010-07-08
That's right, the problem is: I don't really know how to interpret the results.
I captured the packages with Wireshark and I have no idea where to look for errors or something like that.
Is there someone who can tell me what to look for?
For example dropped packages, how do they look like?

A little hint would be appreciated.

thx

---

### Post by spynappels on 2010-07-08
Has some form of QoS been enabled which shapes traffic when a bit-torrent is running?

If you run a continuous ping from the Win-PC to the gameserver, do the latencies increase when you start Transmission?

---

### Post by WinstonChurchill on 2010-07-08
I think this has a lot to do with your ISP and your WAN connection type...

I used to have Cable internet from Time Warner, and the upload speeds were totally abysmal (~30 mbit download, ~0.5 mbit upload), and I had the same issue you do - even if I throttled the upload to 5 KiB/s, COD4 would be totally unplayable, and ping times to Google would be in the 200's.

I recently got Verizon FIOS service (25 down/25 up), and that problem is totally gone. I can completely saturate the upload bandwidth (3 MiB/s) in Transmission, and ping times to Google barely touch 40-50ms (With nothing running, it's around 20ms) - that's with absolutely no attempt at QoS whatsoever. Online games function just fine no matter what I'm doing.

I have a setup very similar to yours - an Ubuntu server acting as the router for my network. I've never tried this (because I haven't needed to), but you could experiment with the NFQUEUE and QUEUE targets in iptables - I think that would enable you to do what you want. Check out the man page. Changing the DSCP and TOS values is pretty pointless - most routers on the Internet ignore those fields altogether, especially lazy ISP's.

---

### Post by endotherm on 2010-07-08
one thing I had to do on my router for simmilar reasons, was to reduce the threshold limits that half established tcp connections have to complete their negotiation, and to increase the number of half formed connections buffered. uses a little more ram, but it works better. I also generally reduce the number of global connections allowed to my client (to like 150) and I throttle the upstream to 30kBps.

here is a great place to start for BT optimization.
[http://ubuntuforums.org/showthread.php?t=1259923](http://ubuntuforums.org/showthread.php?t=1259923)

---

### Post by master-m on 2010-07-08
I will take a look at the QUEUE and NFQUEUE.
Will report the results on Sunday, I think.

Currently I'm running KTorrent on my PC and it doesn't seem to affect the game.

Thank you very much.

---

### Post by arrrghhh on 2010-07-08
rtorrent may work better as well.  I use it on my server, freakin love it.

---

