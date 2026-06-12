---
title: "Weird Internet Issue"
date: 2024-06-01
forum: Ubuntu/Debian BASED
---

### Post by arius88 on 2024-06-01
I'm running Lubuntu 22.04.

Ever since I installed it, I've had this problem with the internet where periodically all my sites stop loading at once; even though the wifi APPEARS to be connected, nothing will work. Usually happens a few times a day. I figured out through trial and error that if I disconnect and reconnect to my wifi, everything starts working again. This has been an annoying work-around but I could live with it. However, the intermittent failure is a real problem now because I am trying to transfer a large number of files from my iPhone over wifi with KDE Connect, and KDE Connect keeps losing the connection to my phone over and over, like every few seconds. It's like pulling teeth just to get a single file to send, and I've got about 4000 of them to transfer, so it's just a nightmare now. 

I'm thinking it has something to do with DNS or DHCP but I really don't even know what those are or how they work or what to do about them.

I tried diagnosing using [this article]("https://linuxconfig.org/how-to-test-internet-connection-on-linux") but found it confusing.

What I was able to ascertain is that pinging an 8.8.8.8 IP seems to work fine, but pinging 192.168.1.1 resulted in 100% packet loss. (That's while the internet appears to be working fine.)

$ ping -c 2 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=118 time=18.1 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=118 time=23.4 ms

--- 8.8.8.8 ping statistics ---
2 packets transmitted, 2 received, **0% packet loss**, time 1001ms
rtt min/avg/max/mdev = 18.098/20.733/23.369/2.635 ms

$ ping -c 1 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, **100% packet loss**, time 0ms


Could really use some help with a) diagnostic guidance and b) resolving the issue once I figure out what the heck is going on. Thanks!

---

### Post by currentshaft on 2024-06-01
Ping is not a useful troubleshooting tool. Next time you experience the issue, look at a packet capture with tcpdump (something like "sudo tcpdump -qni <interface>". Which specific packet type is being dropped or not replied to?

---

### Post by The Cog on 2024-06-02
Maybe you could check that 192.168.1.1 really is the correct address of the router. The command **[FONT=Courier New]ip route list default[/FONT]** will tell you. Most routers will respond to ping so I would normally expect pinging the router to be successful all of the time. 

If the default router really doesn't answer pings then you can use **[FONT=Courier New]sudo arping 192.168.1.1[/FONT]** instead. 

If the ping (or arping) stops working when your connectivity problems occur then the problem is between you and the router - inside the building. If you can still ping/arping the router then the problem is between the router and the rest of the internet. It may be inside the router, but may be anywhere beyond the router, in your ISP or beyond.

---

### Post by arius88 on 2024-06-02
Thanks for the replies so far! Turns out that The Cog's suggestion about having the incorrect router address was right on the money. The "ip route list default" command revealed that my IP is actually 192.168.**4**.1, and I was able to ping that just fine, at least while the internet was working.

Ironically I have had perfect connectivity since posting about it. Bit like a car showing off how good it can run just for the mechanic. But I will stress test it when I have a bit of time this afternoon and should have no problem grinding it to a halt with KDE Connect. I'll try pinging it again then and also see if I can glean anything from using the tcpdump command.

---

### Post by arius88 on 2024-06-02
KDE Connect lost connection with my phone several times while trying to send a few files. 
While that was going on, I went here and tried a couple things: [https://www.comptia.org/blog/7-linux-commands-to-check-network-connectivity](https://www.comptia.org/blog/7-linux-commands-to-check-network-connectivity)

I pinged the IP and a website and it had no problem connecting to those. According to the article, that means that I have connectivity and name resolution.

I tried using tcpdump off and on at different times and it gave me a bunch of output that was gobbledygook to me but looked okay as far as I could tell. Nothing that appeared to be an error. 

I suspect the internet issue and the KDE Connect issue may be two unrelated issues. I'll go on the KDE Connect forums and see if I can get some more specific assistance there. Would still be nice to figure out why all my websites stop loading periodically until I disconnect and reconnect the internet though.

---

### Post by arius88 on 2024-06-02
Update: KDE Connect has been stuck sending the last 0.8MB of a 120MB transfer for about 20 minutes now. For most of that time I ran "sudo tcpdump." When I got bored watching it do its stuff, I pressed Ctrl+C to exit (just found out I can do that today, previously I was manually closing the terminal to get it to stop). It gave me the following output before exiting:

35264 packets captured
124613 packets received by filter
89349 packets dropped by kernel

I don't know what that means, but I assume dropped packets are a bad thing??

---

### Post by arius88 on 2024-06-02
And just now, while the KDE Connect transfer is hung up on that last 0.8%, I pinged comptia.org. It transmitted 16 packets and 14 were received.

---

