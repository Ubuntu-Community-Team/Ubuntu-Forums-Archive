---
title: "IPv6 IPsec encapsulization onion routing? Will it see daylight?"
date: 2008-02-11
forum: The Cafe
---

### Post by Xanderfoxx on 2008-02-11
I have heard of Tor, the Onion Router for some time now, and although it is very good for its purpose, I have to consider that is does not anonymize UDP, RTP, or any other layer-4 protocol. Nor does it allow one to transfer NetBIOS, IPX, Appletalk, or other non-TCP traffic.

I was thinking there had to be a way to dynamically set layered IPsec in a manner similar to the way Tor encrypts TCP traffic.

I have several questions:
[LIST]
[*]What all is involved in starting an Free and Open Source Software project?
[*]What all can be encapsulated on IPv6, besides IPv4? (IPX, AppleTalk, NetBIOS, any other protocols)
[*]What kind of hardware would it take to achieve average ADSL wire-speed with the sending point (directing traffic through multiple dynamically-generated VPN endpoints before entering the WAN connection; also, keep in mind that I intend this to be performed by a dedicated machine running Ubuntu-server)
[*]How much of the host machine's resources would a relay of this kind require to dynamically reconfigure (during runtime), and route IP traffic? (Peak load)
[*]Do you have any comments on this idea?[/LIST]Thank you.

I have thought about this, and I like the idea.

[PC1] {{{ ==== } [R1] ==== } [R2] ==== } [R3] --- --[PC2]

Also, I would like comments on how one might use this technology. How would you use it? Can you think of  any novel ways to use something like this?

How about: Sending icmp echo requests to a friend's computer across town, after instructing her to take down her software firewall, and ask her to try to identify where the pings are coming from? She may say "Oh, yeah, 72.48.185.39, wait! No, it's coming from 75.38.253.68! Oh, okay, fine! They're coming from all over the place."

Or: Playing Warcraft II: Battle.net Edition via IPX-over-IPv6-over-IPv6-...-IP

IPX->IPX/IPv6[x]/IP->IPX

Or even: Encapsulating Tor packets within this system for extra anonymity. Every little bit helps, right?

I think this has potential, but what matters is, do you?

:guitar:

---

