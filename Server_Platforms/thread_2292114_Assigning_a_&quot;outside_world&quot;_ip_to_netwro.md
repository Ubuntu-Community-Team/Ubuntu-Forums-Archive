---
title: "Assigning a &quot;outside world&quot; ip to netwrok/interfaces"
date: 2015-08-25
forum: Server Platforms
---

### Post by tom201 on 2015-08-25
Hello all. Is it possible to assign the outside world address to ubuntu server?

i have a webserver connected to a 5 port switch which connects to my comcast modem. In the past i assigned a static ip to my router but was wondering if i can do away with the router since  the server is the only machine running on that static ip. 

Nano'ing the network interfaces file i did this

                   static
address xxx.xx.60.241
broadcast 255.255.255.0
gateway xxx.xx.60.246

resolve conf always shows the right dns servers so i didnt mess with it

i have your standard comcast modem with 5 statics assigned to me from comcast

thank you in advance-tom

---

### Post by TheFu on 2015-08-25
TL;DR - yes you can. No, you shouldn't.

I have the same Comcast setup - 5 static IPs.
I do NOT directly assign these IPs to any servers - it is a security consideration which starts at the network design. A server directly connected to the internet is that much more hackable than a server behind a separate firewall.  Making mistakes with firewall rules is common on computers.  It is common on routers too, but on computers, we tend to leave them too open. On routers, too closed. I'd rather be closed than open.

If you have a comcast provided router, I have an SMC, you can put that router into bridge mode simply by having your personal router WAN interface take all the public IPs, have the correct netmask and use the gateway IP owned by the comcast router.  Nothing says you can't make that edge device be your Ubuntu (or any) computer, besides security considerations. You CAN do you. IMHO, you should NOT do it.

I want as many barriers to an attacker as I can get. The comcast router is worthless for that, since they don't let us touch - look, don't touch - but my router is not.  The router is monitored, tracks bandwidth, blocks brute force attacks, syn attacks, runs a VPN, and passes selected ports as selected static IPs, to selected servers on the server LAN. More secure that way.

Of course, my personal devices and family devices are on 2 other LANs - never let teen devices be on any network you need to be virus free.  I don't want any desktops on the same LAN as internet facing servers either. Security design is a well-worn area - just pay attention to what others have done before to avoid most common mistakes ... er ... like putting a server directly on the internet.  We can do better than that.

---

### Post by tom201 on 2015-08-25
Your reply runs along with what i was thinking. I have many reasons for skipping the router but the main idea i had was to run all traffic thru one server to filter out bad ip's i have on my iptables list. I too have alot of bad traffic coming my way and was thinking the routers (everyday routers-cisco) are a weak link. i run some game servers on my boxes and i am a magnet for dos attacks.

---

