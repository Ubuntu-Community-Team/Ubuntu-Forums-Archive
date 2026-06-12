---
title: "BitTorrent Developers Introduce Comcast Busting Encryption"
date: 2008-02-17
forum: The Cafe
---

### Post by stalker145 on 2008-02-17
[http://torrentfreak.com/bittorrent-devs-introduce-comcast-busting-encryption-080215/](http://torrentfreak.com/bittorrent-devs-introduce-comcast-busting-encryption-080215/)

> Several BitTorrent developers have joined forces to propose a new protocol extension with the ability to bypass the BitTorrent interfering techniques used by Comcast and other ISPs. This new form of encryption will be implemented in BitTorrent clients including uTorrent, so Comcast subscribers are free to share again.

BitTorrent throttling is not a new phenomenon, ISPs have been doing it for years. When the first ISPs started to throttle BitTorrent traffic most BitTorrent clients introduced a countermeasure, namely, protocol header encryption. This was the beginning of an ongoing cat and mouse game between ISPs and BitTorrent client developers, which is about to enter new level.

Unfortunately, protocol header encryption doesn’t help against more aggressive forms of BitTorrent interference, like the Sandvine application used by Comcast. A new extension to the BitTorrent protocol is needed to stay ahead of the ISPs, and that is exactly what is happening right now.

Back in August we were the first to report that Comcast was actively disconnecting BitTorrent seeds. Comcast of course denied our allegations, and ever since there has been a lot of debate about the rights and wrongs of Comcast’s actions. On Wednesday, Comcast explained their BitTorrent interference to the FCC in a 57-page filing. Unfortunately they haven’t stopped lying yet, since they now argue that they only delay BitTorrent traffic, while in fact they disconnect people, making it impossible for them to share files with non-Comcast users.

In short, the Comcast interference works like this: A few seconds after you connect to someone in a BitTorrent swarm, a peer reset message (RST flag) is sent by Comcast and the upload immediately stops. Most vulnerable are users in a relatively small swarm where you only have a couple of peers you can upload the file to.

For the networking savvy people among us, here’s an example of real RST interference (video) on a regular BitTorrent connection. In this case, the reset happens immediately after the bitfields are exchanged. Evil? Yes - but there is hope.

The goal of this new type of encryption (or obfuscation) is to prevent ISPs from blocking or disrupting BitTorrent traffic connections that span between the receiver of a tracker response and any peer IP-port appearing in that tracker response, according to the proposal.

“This extension directly addresses a known attack on the BitTorrent protocol performed by some deployed network hardware. By obscuring the ip-port pairs network hardware can no longer easily identify ip-port pairs that are running BitTorrent by observing peer-to-tracker communications. This deployed hardware under some conditions disrupts BitTorrent connections by injecting forged TCP reset packets. Once a BitTorrent connection has been identified, other attacks could be performed such as severely rate limiting or blocking these connections.”

So, the new tracker peer obfuscation technique is especially designed to be a workaround for throttling devices, such as the Sandvine application that Comcast uses. More details on the proposal can be found at BitTorrent.org, which aims to become a coordination platform for BitTorrent developers.

TorrentFreak talked to Ashwin Navin, president and co-founder of BitTorrent Inc. who has some of his employees working on the new extension. He told us: “There are some ISPs who would like people to believe that “slowing down” BitTorrent or “metering” bandwidth consumption serves the greater good. Consumers should be very weary of this claim.”

“In recent months, consumers enjoyed unprecedented participation in the political process thanks to the ability to upload opinions and feedback in the YouTube presidential debates. Musicians, filmmakers and artists are finding ways to connect with their audiences across the world thanks to MySpace and BitTorrent. Students are engaging with interactive learning tools in their schools. Which bandwidth intensive application will banned or shaped or metered next by these ISPs? The creative spirit of millions has been ignited, and our need to participate, to communicate will not be silenced.”

“The US government should encourage ISPs to innovate and invest in their networks,” Ashwin said. “Permitting them to interfere or interrupt in the communications of consumers, to protect ISP profit margins, would be a tremendous set back for our country and economy, when we are already slipping behind the first world (UK, EU, Japan, Korea, Singapore, etc) in its broadband capacity.”

We wholeheartedly agree with Ashwin on this one, as we’ve said before. The Internet is only a few years old, if the plan is to keep using it in the future, ISPs need to upgrade their networks. So, invest in more Internet gateway capacity, 10Gbps interconnect ports, and peering agreements. BitTorrent users are not the problem, they only signal that the ISPs need to upgrade their capacity, because customers will only get more demanding in the future. The Internet is not only about sending email, and browsing on text based websites anymore.

The new protocol extension is still under development, but the goal is of course, to get it out as soon as possible.

Hang on…

Many links in the original article.

---

### Post by zmjjmz on 2008-02-17
Will there be an update of this through the Ubuntu update manager?
And will Azureus get this?

---

### Post by EXCiD3 on 2008-02-17
This sounds promising, but how far into development are they i wonder? This is a really cool idea and would help bittorrent out a lot seeing as comcast is such a large provider.

If this is officially released, any up-to-date torrent program should have support for it including transmission, ktorrent, and azureus. I cant wait!

---

### Post by Polygon on 2008-02-17
nice, as a comcast user, i cant wait =P

---

### Post by Kimm on 2008-02-17
Seeing as µTorrent gets it, libtorrent probably will too and thus also Deluge/qBitTorrent.

---

### Post by gsmanners on 2008-02-17
This is a temporary fix for a political problem. The real problem is that Comcast wants P2P in its entirety shut down so they can monopolize streaming video. Hopefully, folks like Blizzard and BitTorrent can convince the FCC to not look the other way on this issue.

---

