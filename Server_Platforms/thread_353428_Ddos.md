---
title: "Ddos"
date: 2007-02-04
forum: Server Platforms
---

### Post by b0red on 2007-02-04
Hi All,
One of my servers is getting DDOS'd by persons unknown and I'd like a sanity check one what I've done.

Essentially we seem to be getting SYN flooded by a few hundred bots, both on ipv4 and ipv6. I have disabled ipv6 support as I don't need it and it appreas to 'double' the syn flooding.

Basically I have quite a lot of these kind of entry :
roto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 web01:www                home-323019.b.astr:2154 SYN_RECV
tcp        0      0 web01:www                home-323019.b.astr:2153 SYN_RECV
tcp        0      0 web01:www                69.81.253.208:3422      SYN_RECV
tcp        0      0 web01:www                193.25.111.148:2489     SYN_RECV
tcp        0      0 web01:www                195.182.220.119:3611    SYN_RECV
tcp        0      0 web01:www                85.120.82.251:4446      SYN_RECV
tcp        0      0 web01:www                home-323019.b.astr:2146 SYN_RECV

There were also many ipv6 entries as well.

I have enabled syn cookies but it did'nt help much as there were quite a few hosts attacking. I also have enabled mod_evasion .
The firewall does SYN flood protection as well as other types of DDOS but it does'nt seem to help much. Even though the firewall does SPI it only really seems to rate limit the number of packets / sec it allows through.

I'm also getting this, where I have large numbers in the Recv-Q but nothing in Send-Q I'm blocking the IP at the firewall , I'm afraid on the basis 'it looks strange' rather than knowledge of what it is actually doing. Does this seem reasonable? 

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 localhost:mysql         *:*                     LISTEN
tcp        0      0 *:www                   *:*                     LISTEN
tcp        0      0 web01:www                ip70-178-194-45.ks:1747 SYN_RECV
tcp        0      0 web01:www                ip70-178-194-45.ks:1746 SYN_RECV
tcp        0      0 *:ssh                   *:*                     LISTEN
tcp        0      0 *:smtp                  *:*                     LISTEN
tcp        0      0 web01:www                ip70-178-194-45.ks:1694 TIME_WAIT
tcp        0      0 web01:www                ip255-121-173-82.a:2277 TIME_WAIT
tcp        0      0 web01:www                ip255-121-173-82.a:2302 TIME_WAIT
tcp      537      0 web01:www                ip-80-236-194-128:15939 ESTABLISHED
tcp      523      0 web01:www                ip-80-236-194-128:15941 ESTABLISHED
tcp      525      0 web01:www                ip-80-236-194-128:15940 ESTABLISHED

---

### Post by Patrick-Ruff on 2007-02-04
can you limit the number of access attempts?  if you can, 3-4 access attempts per bot (perhaps you could even program something to make it lag the bot as it waits for a response so they could get a couple hundred attempts and then suddenly stop ;) )

forgive me if my idea's are illogical, I don't know much about servers, but it seems like a good idea to me.

---

### Post by Brazen on 2007-02-05
> **Patrick-Ruff said:**
> can you limit the number of access attempts?  if you can, 3-4 access attempts per bot (perhaps you could even program something to make it lag the bot as it waits for a response so they could get a couple hundred attempts and then suddenly stop ;) )

forgive me if my idea's are illogical, I don't know much about servers, but it seems like a good idea to me.

there is iptables rules to limit the number of connections.  You could even have it apply only to SYN packets.

---

### Post by dahas on 2007-04-02
for stoping this i do this 
ip ro add ip_who_flood/32 dev lo

in this way server will drop respons to lo and the attackers think is down server (dont get any respons) the proble is after a while i get another ip who do same try all ports and send same **** to them.
The resons come from ISP who supose to take an announce in front of me about that rute to wont past his networks any more till the problem is not solved.
Here some ip-s of attacks i can update this list with 2-3 new ip / day / server
60.12.192.3 
24.143.87.60
83.103.136.150

I try the limit with iptables but is waste of time as long my server respond attack will continue.
Thinking to cut the echo port to see if i my not respond at echo mybe wont start attack :D just thinking i will test and as soon i get a proper resons to give u hint

---

