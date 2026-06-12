---
title: "Does anyone have experience with the Deeper Network VPN/Firewall?"
date: 2021-03-17
forum: The Cafe
---

### Post by MoebusNet on 2021-03-17
I just pulled the trigger on this Indiegogo-funded hardware ([https://deepernetwork.net/](https://deepernetwork.net/)) the Nano model; I was curious to see if the community had any experience with it. This is supposed to be a Distributed Virtual Private Network and firewall combination box that is placed between your LAN and the Internet. Mashable had it on sale, and the thought of having a VPN with no subscription fees was too much for me. I liked the idea of a P2P-type distributed model VPN with no central server & logs.

So anyone tried this yet?

---

### Post by DuckHook on 2021-03-17
I'd heard about them, but your link was the first time I've ever bothered to look at their device. It's an interesting concept. My biggest concerns would be threefold:

[LIST=1]
[*]What's the throughput? Since it relies on a network of SOHO users, I might find any given session being funnelled through a rinky-dink 200 Kbps ADSL line.
[*]What does this mean for my data usage? Especially if I'm on a limited/expensive data plan?
[*]How does the technology stop the endpoint from sniffing my data? Granted, the same problem plagues TOR, but the TOR tri&#8209;segment design conceptually provides some anonymity (provided I use it properly). Is the DPN protocol similar? Or is it just point to point?
[/LIST]
I'm strongly sceptical of their claim that they are "better than traditional VPNs". Even TOR which has been around a lot longer is way slower than my VPN provider with its paid terabit backbone connections. It isn't possible for the sort of tech that Deeper relies on to be performatively equal. Such hyperbole just diminishes their credibility.

---

### Post by DuckHook on 2021-03-17
Upon thinking this through more carefully, a number of other serious questions come to mind:

[LIST]
[*]Are you okay with the authorities tracing illegal torrents and kiddie porn images back to your IP address? Because I suspect that this may be some of the traffic that will be going through your new router.
[*]Are you okay with 100 GB torrents hogging your bandwidth? Because I don't see how the DVPN protocol can prevent this.
[*]Are you okay with attracting the attention of big three&#8209;letter agencies of various nation states because people they consider dangerous or subversive are "borrowing" your IP address to plan their activities? Because I think that's gonna happen too. As will criminals, drug cartels and other scumbags.
[/LIST]
The more I think it through, the more this gives me the willies.

---

### Post by MoebusNet on 2021-03-18
I share your concerns. I've been running barefoot (no firewall, no VPN) for years and the more I read about security concerns the more confused I become. All the good reasons to use a VPN are moot if you can't trust the provider. If you go online at all, your IP address, your MAC address and your identity can all be spoofed. That's why I thought this might work.

This whitepaper ([https://www.deeper.network/whitepaper_en.pdf?1616066483915](https://www.deeper.network/whitepaper_en.pdf?1616066483915)) outlines what sounds like a reasonable concept to safeguard privacy and share bandwidth equably.

Unlike many, the only thing that runs 24/7 on my LAN is my television PVR. Everything else stays power-off unless I am actively using it. Apparently, this device will want to be online 24/7 also. Internet connectivity is so poor at my location that I rarely see above 100 KB/s download speed, let alone upload speeds of trivial or less. I figure if this device doesn't work for me, I'll put it on Craig's list or whatever an see what I can recover. I may try to leave the device unpowered except when I'm online.

I noticed that because of bitcoin token mining, the company has made an effort to avoid bandwidth-hogging behaviors. We'll see how that works...

---

### Post by DuckHook on 2021-03-18
In the odd way that coincidences work, I just posted on the subject of trust on another thread. No point in repeating myself, but if interested: [https://ubuntuforums.org/showthread.php?t=2459397&p=14026822#post14026822](https://ubuntuforums.org/showthread.php?t=2459397&p=14026822#post14026822)

Do let us know what your experiences are. Though I have my reservations, I'm also curious.

---

### Post by MoebusNet on 2021-03-19
Also in the odd way coincidences work, for some reason Mashable cancelled my order - something about they weren't able to verify that it was really me that placed the order. They did, however, offer to allow me to reorder. Perhaps this is simply coincidence, perhaps a sign from the Universe, but I think I'll just skip the whole business for now. Deeper Connect's website mentioned something about a Pico model (not available yet) to follow the Nano (which was on sale in limited quantities). If and when the new model comes out I may revisit this whole idea. I guess for now I'll keep my money in my pocket and see what else is interesting. Thank you for the perspectives on security; good information.

---

### Post by DuckHook on 2021-03-19
:lolflag:
Signs from the higher IT powers must be heeded!

You may wish to look into TOR. Running an exit node on your limited bandwidth is not feasible, but routing everything through TOR might give you the anonymity that you seek. But it's important to note that anonymity is 90% personal conduct and only 10% technology. Well, that's a quantification fallacy because the details are more subtle and ambiguous, but I hope I'm conveying some sense of the proportionality.

Details here: [https://www.wikihow.com/Setup-and-Use-the-Tor-Network](https://www.wikihow.com/Setup-and-Use-the-Tor-Network)

A word of caution: TOR is slow. Setting up your computer so that everything gets funnelled through TOR will incur a huge performance hit.

---

### Post by MoebusNet on 2021-03-20
I already use TOR on occasion; have done since the U.S. Navy published an onion router service way back in the dark ages. I boot from a Live-DVD (no persistence) when the occasion warrants. I guess I was just looking for a shortcut to avoid having to:

1) Learn IP tables and firewall ports administration

2) Research,purchase and administer a VPN service

3) Schedule my time around maintaining items 1 & 2.

All this just to have a bit more confidence that I'm slightly less likely to be ripped off or abused (sigh). There's gotta be a better way, if we can just figure it out!

---

### Post by DuckHook on 2021-03-20
> **MoebusNet said:**
> 1) Learn IP tables and firewall ports administration
No need to learn IP tables directly. But since you are directly connected to the Internet, it is highly advisable for you to install GUFW, which is a GTK frontend to UFW and makes firewall admin relatively painless.
> 2) Research,purchase and administer a VPN service
ProtonVPN has a free tier. It's quite restricted and probably oversubscribed, but nonetheless one of the few that deserve a certain level of trust. I don't use it, but it's both FOSS (client) and third&#8209;party audited.
> 3) Schedule my time around maintaining items 1 & 2.
I don't see too many time sinks or maintenance headaches. Once the initial firewall has been set up, it's pretty much let it run and otherwise forget about it. Likewise, VPN services come with their own apps these days which make start/stop/admin quite easy.
> All this just to have a bit more confidence that I'm slightly less likely to be ripped off or abused (sigh). There's gotta be a better way, if we can just figure it out!
'Fraid not. The biggest issue with ripoff/abuse is the entity between the keyboard and the chair. No technology or vendor or platform will solve that problem. I've never discovered an out of box no&#8209;brainer solution to this need. Every measure that I've ever implemented to increase privacy or anonymity or security has come at the expense of convenience, ease and simplicity. That's the tradeoff I'm afraid we have to live with.

---

### Post by MoebusNet on 2021-03-20
Got it: GUFW, Proton VPN, use common sense when surfing.

Any views on the inclusion of Wireguard VPN in the Linux kernel together or separately with TOR? They've got something called TORguard now which I think combines the two.

---

### Post by DuckHook on 2021-03-20
> **MoebusNet said:**
> …Any views on the inclusion of Wireguard VPN in the Linux kernel together or separately with TOR? They've got something called TORguard now which I think combines the two.
Wireguard is very exciting. I'm looking forward to learning its ins and outs. It hearkens back to Linux's roots as a highly efficient, highly elegant solution that does one thing and does it exceptionally well. It is very tightly coded, numbering only 2% of the codebase of OpenVPN, which makes it much easier to audit, test and maintain. The problem with Wireguard for now is that it is really only at beta or post&#8209;beta stage. I know that this will raise the hackles of a lot of its fans (including Linus Torvalds himself), but that's the way I see it. It only works through UDP, has no TCP implementation and has not yet been rigorously security stress tested. Some think that Linus jumped the gun including it in the kernel. I'm happy to see it there, but one should be aware of just how brand spanking new it is. By contrast, even though OpenVPN is slower, lumbering and 50 times as obese, it has been time&#8209;tested and, to my knowledge, passed every such test with flying colours. I consider them both excellent—in fact, the only permissible—choices for me.

TORGuard is, I believe, merely another commercial VPN provider that had the (smart) idea of leveraging the TOR name to enhance their brand, hoping for some knock&#8209;on effect. I suppose they have largely succeeded, at the cost of confusing the market into conflating their product with the larger TOR ecosystem. However, AFAIK, they don't offer anything that is much different than other VPN providers. I considered them when switching from my old VPN provider, but didn't like the way they exploited TOR by riding on their coattails, so settled for another provider.

The choice of VPN providers is important—one is tempted to say, crucial. I find that, because most of them are commercial enterprises, there can be a lot of shady business behind closed doors. I left my last VPN provider because they sold out to a new owner whom I consider highly untrustworthy/unethical. Prior to that, they were one of the few who had been taken to court by a three&#8209;letter agency and hence publicly proved to have been as good as their word in not keeping logs of any kind. It's an ever evolving landscape, which is another reason why privacy/anonymity/security can't be a simple system that we just install and forget.

---

### Post by DuckHook on 2021-03-20
> **MoebusNet said:**
> Got it: GUFW, Proton VPN, use common sense when surfing&#8230;
A further thought and then I'll let go of this bone.

I'm afraid that "common" sense is no longer enough. Those were the good old days. With the advent of phishing, spear&#8209;phishing, profiling and ID theft rings, one is forced to learn and practice ***un***common sense. That's what makes modern safe computing so hard. You can take some small comfort in knowing that your frustration with the difficulties of security are shared by me and practically everyone else who knows enough to wrestle with it.

---

