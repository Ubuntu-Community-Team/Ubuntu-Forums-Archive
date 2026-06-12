---
title: "No legal HD content in Ubuntu?"
date: 2006-02-14
forum: The Cafe
---

### Post by joflow on 2006-02-14
Someone please help me understand HCDP and what it might mean for the future of High Def content in Linux?

[http://arstechnica.com/articles/paedia/hardware/hdcp-vista.ars](http://arstechnica.com/articles/paedia/hardware/hdcp-vista.ars)

One of the more touchy subjects crowding my inbox lately relates to how Windows Vista will fail to render High Definition video in "pure" High Definition on most existing monitors. There's quite a bit of hemming and hawing over the probability that Windows Vista users will have to buy new monitors to see HD content. Let's get a few facts out on the table before we oil our rags and tie them to our spears, because there's a considerable amount of misinformation out there.

First of all, High Definition content is not what you get on a DVD today. Most DVDs are 480i (upsampled to 480p by many quality players), the same as broadcast TV (but without the distorted colors). HD content is essentially everything above the 480 lines: 720p, 1080i, and 1080p (the last one is currently rare).

With rare exception, right now there's only two ways you are watching commercial HD content legally (I'm not including BitTorrent or USENET in this example): you're either grabbing it from over-the-air (OTA) signals, or your cable/satellite provider is sending it to you, guarded by their set-top boxes. Let me point out the takeaway: the content is supposed to be secured. Video from the cable/satellite providers is encrypted and protected. The OTA content is not encrypted, but let's not forget that the broadcast flag was designed in order to add DRM controls to OTA transmissions. As far as the content industry is concerned, both channels of distribution need to be secured.

But there's a catch. The old adage that if you can see it, you can pirate it, sticks in the craw of the content industry. To make matters worse, DVI delivers high-quality, essentially perfect video. While great for us, it's also great for counterfeiters who can use DVI to get at a pristine video signal, regardless of DRM enforcement. This is the background to the birth of High-bandwidth Digital Content Protection (HDCP). Developed by Intel, the technology provides a two-part cryptographic scheme to control video transmission and delivery at the very end of the video display process. Technically speaking, HDCP is content protection, not copy protection. Restrictions on time-shifting, copying, sharing, etc., will all be handled by the likes of cable/satellite boxes, DRM schemes, and the like. HDCP, in short, simply guarantees that whatever content restrictions are in place are enforced by authenticating both the transmitter and the receiver. (For more information, see this great article describing how this works in the 1.0 specification.)

The upshot of all of this is that display devices need HDCP support. If a monitor or television supports HDCP, HD content will be playable on that device (provided that it hasn't been cracked). If a monitor doesn't support HDCP, one of two things will happen at the discretion of the content providers. It's a possibility that a given studio may simply refuse to allow the content to be displayed at all. More likely, the studios will allow for playback on unauthenticated devices with purposely degraded quality. The thinking is that Joe Consumer will be more likely to pay for HD content than seek out pirated content that's not in HD. Talk around the industry suggests that many studios will degrade content to a 480p level by passing it through a constrictor, although we won't really know until products start shipping.

Now, HD DVD is already on board with HDCP (although HD DVD looks like it's dying), and Blu-ray is expected to follow suit, since HDCP is already supported by many high-end HD TVs now in the market. Those that doubt Blu-ray's eventual support for HDCP should keep in mind that the Blu-ray Disc Association (BDA) recently began touting itself as more secure than HD DVD, adding BD+ and ROM-Mark as a compliment to AACS. HDCP is a reality of the future market.

Where does that leave Microsoft? It leaves Microsoft in the same place it leaves everyone else in the consumer electronics industry. The company, which as you may know includes a Media Center amongst its products, obviously wants to be able to support the playback of true HD content, and this means that they have to support HDCP (and they will, across their entire OS line). Or, let me phrase this in another, more contentious way: if you think Apple is going to turn down HDCP despite being DRM advocates themselves (Hello, FairPlay!), with the result being that it will be impossible to view new content in full HD on Apple hardware, then you're kidding yourself. DRM in this context is unacceptable, in my opinion, but the studios (so far) are entitled to license their content however they want, and anyone who wants in the game will have to follow suit. This is the equilibrium that exists in the market today, and barring legislation to the contrary, it's going to stay that way.

Marcus Matthias, product manager of Windows Digital Media at Microsoft, informed me that Microsoft is committed to Windows offering all the benefits of consumer electronics devices, and this means fully supporting the specifications in play in the consumer electronics arena.

    "Any device—whether it be a PC or consumer electronic device—will need to ensure compliance with the specified policies otherwise they risk being unable to access the next-gen DVD content. Clearly we think that offering next-gen DVD content on the PC is much preferable to having the PC excluded from accessing this premium content," he said.

Indeed, Microsoft doesn't really have a choice, and neither does Apple. In fact, if you've been following this game, you'd know that the only reason we're not already stuck in this quagmire is because PC DVD players were grandfathered in, and are exempt from upsampling rules.

So yes, Microsoft is a bit ahead of the curve on this, but that's partially because of their (very long) development cycle—we are talking about an OS that's at least 14 months away (my guess). And while PVP-OPM (Protected Video Path-Output Protection Management)—which provides a secure path from applications to HDCP output —isn't entirely finalized, the general framework is a certainty.

Apple will be on board too, possibly with the release of Leopard (Mac OS X 10.5). Tiger saw the light of day in April, and with the company intending to release Leopard around the same time as Vista, that means that we'll be seeing HDCP support on the Mac (powered by Intel!) probably around the same time as the release of Windows Vista. And until then, we'll all be scratching our heads as to how our Linux friends will solve this quandary, because HDCP has to be commercially licensed. Well, that is unless DVD Jon swoops in again, but cracking BDA's discs won't be as simple as cracking CSS.

Finally, while we're all in lynch mode, let me add the last anti-hurrah. TVs without HDCP, also known as most TVs in North America, are subject to the exact same problem. In 2004, HDTV penetration in the US was estimated at 9 percent. Of those TVs, most of them do not support HDCP (although TVs sold today do, by and large). However, if you're heading out this weekend to drop US$3,000 on a TV, chances are high that it will support HDCP. The same can't be said of monitors, sadly. Apple's US$2999.99 30" display doesn't support HDCP, and only a handful of Dell's various options do. If you're in the market for a new display, you might want to wait until some units are shipping with HDCP support. You might think that you'll be able to buy an HDCP stripper, but there's a problem there. Once a stripper hits the (black or white) market, all a content provider needs to do is revoke the keys used by the device. It's not a solution. Between Blu-ray's BD+ and HDCPs key revocation, this next generation of tech is going to be considerably harder to crack.

The revolution will be televised, only it won't be in HD unless your pockets have paid for recent display technology designed with the future in mind.

---

### Post by joflow on 2006-02-14
I'm concerned about this part of the article:

"and until then, we'll all be scratching our heads as to how our Linux friends will solve this quandary, because HDCP has to be commercially licensed."

It seems that HDCP is primarily hardware DRM and blueray/hd-dvd players will be designed to work with it.  If there is no HDCP or if the OS provides no way for the hardware to determine if there is HDCP then that means HD content (whether legal or not) will be downscaled to 480p.

Since HDCP has to be licensed, we can assume it won't be in Ubuntu (like the MP3 codec or other software that needs licensing).

So does that mean there will be no legal HD content in Linux?

---

### Post by aeiah on 2006-02-14
there'll be no legal HDCP content, but then, who wants HDCP (High-Bandwidth Digital Content Protection) when high defenition unprotected, free (as in free to use without a microsoft / intel tax) will be available with the click of a download button, or the installation of a crack, or the plugging in of a filter? HDCP has already been decrypted and whilst The Powers That Be can lock and blacklist your hardware, there will be methods for unlocking, or blocking the block. the content protection scheme in this instance is protecting hardware manufacturers from competition far more than it is anything somewhat more valid, such as the film industry.

i try to avoid DRM wherever possible and thankfully, there is a lot of others that feel the same

---

### Post by mstlyevil on 2006-02-14
These two threads have already been disscussing this issue.

[HDCP in Ubuntu?]("http://www.ubuntuforums.org/showthread.php?t=129519")

[WTF!!!!! They lied to us!! Meanies]("http://www.ubuntuforums.org/showthread.php?t=129214")

---

### Post by Stormy Eyes on 2006-02-14
Let them have their DRM. I'll crack it, because I claim the right to as I will with my hardware and the media I have purchased. If they don't like it, they can discuss it with my sledgehammer.

---

### Post by joflow on 2006-02-14
[QUOTE=mstlyevil]These two threads have already been disscussing this issue.

[HDCP in Ubuntu?]("http://www.ubuntuforums.org/showthread.php?t=129519")

[WTF!!!!! They lied to us!! Meanies]("http://www.ubuntuforums.org/showthread.php?t=129214")[/QUOTE]

Thank you.

---

