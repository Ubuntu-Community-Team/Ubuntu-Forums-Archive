---
title: "VPN Usage"
date: 2014-01-09
forum: The Cafe
---

### Post by NertSkull on 2014-01-09
So I always get great advice from people on these forums, so I thought I'd ask this question here.

I'm just getting into the VPN world and I have one big question on how to use it.  Is there any danger in passing ALL your traffic through a VPN?

Details:

I'm not doing anything crazy or illegal.  I just don't like the idea of my ISP looking into everything I do. But I also seem hesitant to do my online banking/personal email through a VPN.  I don't know, but for some reason it seems like "bad" people would pay more attention to a VPN exit node trying to intercept traffic.  I know my bank/email is SSL/TLS encrypted type stuff.  So I know in theory it shouldn't matter.  But I can't help but feel that I'm becoming more noticeable by doing it from a VPN exit instead of just lost in the masses of regular people using their ISP.

I'm I being overly paranoid? Is there realistically no difference between using the VPN vs my ISP to access the internet at large?  

For example, lets take unencrypted data, like posting in a forum.  I recognize on my ISP anything I do can basically be seen by others willing to take the time.  But I would make the assumption that if I post in the same forum through a VPN it might get just a bit more notice and scrutiny as a potential target than the same material coming from an ISP.  Is that a completely horrible assumption?

I guess this comes from polls I've seen asking people how they use there VPN.  And most people appear to only "connect occasionally".  Why not ALWAYS connect and send ALL your data through it?  I recognize some people are trying to hide.  But the matter still applies.  Why not send ALL your data through the VPN, and then when you want to 'hide' connect to a different exit server for complete anonymity? You can get the best of both worlds that way.  VPN privacy for day-to-day stuff from your ISP.  Anonymity when you want it for "other activities".

Sorry for rambling, I'm not sure I'm making my concerns clear enough.  But I'd love to hear some thoughts on the matter from the community.

VPN all your traffic all the time?

---

### Post by TheFu on 2014-01-09
Seems like you have a good understanding of what VPNs do and don't do.

The main reasons NOT to use a VPN are:
* cost
* slower internet
* technical difficulty in setting it up

HTTP/SSL is based on trust - trust in the DNS provider(s) and trust that not-a-single-CA anywhere in the world violates that trust.  In short, it is broken.  If you use the internet inside your own country and bank inside your own country, then there isn't much concern using the internet from a reputable ISP from your home/office.  No way would I trust HTTPS when in a different country.  I've seen where country-wide monitoring and proxies were used.  During a trip to Asia in Nov/Dev, connectivity to my home web server was filtered by most ISPs in the country, but ssh, imaps, smtps worked fine. It happened from every wifi I connected in that country, including at the airport in a lounge.  Oddly, using the state-owned cellular system, access to my home web server worked perfectly.  Also, from other "more western" countries in the trip, everything worked fine.  

There are technologies that dynamically create certs that look find to our browsers and desktops when a normal HTTPS connection is needed. Those devices look at all traffic inside, then reconnect to the service. The end-to-end encryption is broken. That is the issue with using encryption methods based on trusting many 3rd parties.  You seem to know this already.

VPNs are mainly useful when away from home or when you don't want the network provider to see where you go.  Don't forget that DNS lookups AND URLs are not encrypted under web browsers, so all that traffic is known by the network provider even if HTTPS is used.

VPNs are also used for illegal stuff. When that happens, usually the VPN exit node will be in a different country. I know a few people who have exit nodes in Romania. I can only guess why.

For my needs, running a VPN from wherever I am in the world (or just down the street) back to my home is the best solution. It provides the desired privacy when I'm away, but not when sitting on my trusted network. No need for a paid service or providing my financial information to some 3rd party. Plus, since I run the VPN server, it I don't need to trust some 3rd party with my keys.  I create the keys and I keep them.  TNO - Trust No One.  Obviously, I trust the OS makers, the software devs, the testers, and my DNS provider.  However, with me having control over both sides of the keys, I don't have to worry that someone else is intercepting my traffic and decrypting it. No worry about MiTM attack vectors either, since if the public and private keys don't match, then the connection will fail. I'd rather have a failed connection.

Whatever you choose, please DO NOT use pptp, it has been broken a few times. OpenVPN and ssh are about the only network encryption I'd trust.  I'm worried about ssh, but haven't seen any concrete reason.

No, I don't VPN my traffic all the time, just when I'm away from home.

---

### Post by mastablasta on 2014-01-10
yean VPN is connecting to your home network from distance. for example i want to share some files or doa project with my bro we connect and create our own VPN. so it's faster than mailing back and forth.
but mostly we just use it to play some old games. i turn it off when not using it.

---

### Post by sammiev on 2014-01-10
I use SSL VPN most of the time and DENY all in and out bound within the firewall. Then I have only the out bound ports open that I need. 

This is the profile I use when I'm home. On the road I use another profile with tighter rules.

```
sam@linux-f07s:~> sudo ufw status
root's password:
Status: active

To                         Action      From
--                         ------      ----
80/tcp                     ALLOW OUT   Anywhere
443/tcp                    ALLOW OUT   Anywhere
25/tcp                     ALLOW OUT   Anywhere
110/tcp                    ALLOW OUT   Anywhere
143/tcp                    ALLOW OUT   Anywhere
67:68/udp                  ALLOW OUT   Anywhere
123/udp                    ALLOW OUT   Anywhere
1194/udp                   ALLOW OUT   Anywhere
53                         ALLOW OUT   Anywhere
1723                       ALLOW OUT   Anywhere
631                        ALLOW OUT   Anywhere
515                        ALLOW OUT   Anywhere

```

---

### Post by nilla78ro on 2014-01-10
If you really want to use a VPN , it can improve your browsing speed :confused:( as a side effect you will be anonymous for your ISP) , the condition is that you should have a good connection to that server! , because it is in a data center and it have a better connectivity than you @ home.

---

### Post by bashiergui on 2014-01-10
> **nilla78ro said:**
> If you really want to use a VPN , it can improve your browsing speed :confused:( as a side effect you will be anonymous for your ISP) , the condition is that you should have a good connection to that server! , because it is in a data center and it have a better connectivity than you @ home.
What? No you won't be anonymous to your ISP at all. They will see your DNS requests from your actual IP. They will see there is traffic to the VPN from your real IP. They just won't be able to see the *contents* of the traffic. 

There is no anonymity in a VPN unless you couple it with Tor.

---

