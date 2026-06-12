---
title: "Why I think Linux should have one commercial media player"
date: 2008-10-23
forum: The Cafe
---

### Post by bash on 2008-10-23
At the moment if you want to watch a DVD of some Hollywood you are only able to do so by using means that are illegal in most countries. For the upcoming spread of Blu-Ray the situation looks even more dire.

Personally I agree that the ideal situation would if those formats wouldn't have any encryption at all and/or would be openly documented so that *insert favourite player here* could easily implement the support. But sadly that doesn't seem to be a realistic situation in the near future. Even if Linux adoption would suddenly be around 20% of the market, I just think that just more commercial video player would start to appear, instead of open formats.

So that is why for now I would favour if that would one commercial media player just specifically for the playback of all the encrypted formats (DVD, HD-DVD, Blu-Ray). I know there exists LinDVD but AFAIK that doesn't even have support for the HD media. Further it looks like a cheap 1:1 port of the windows version in GTK+ 1 and therefore looks ugly and completely out of place.

What I would wish for would a small, light-weight application with a simple and clean interface. It should just handle playback of those media types and try to be some one-to-rule-them-all-player. Also it should be a Linux program, build on Linux technologies (D-Bus, GStreamer, PulseAudio, ...) and using them for benefit. Preferably it should be separated in a back-end that handles all the decoding/playback and different front-ends. So there could be one written in GTK+ for GNOME & Xfce users, one in Qt for our KDE friends (and even one in Tk for those who like ugly ;)). 

If a program like that existed, that gave you the chance for legal playback and would be shipped for around 20 - 25&#8364; I and quite a few people I know would immediately buy it. But as said it would be important it doesn't just feel like some cheap port of a windows app to shell out another few bucks from the Linux users. 

So for the normal media playback (video files, music, ...) everyone would still use *insert favourite player here*, while for the those 3 disc formates you could rely on the Linux Proprietary Media Player.

---

### Post by sethvath on 2008-10-23
[http://www.itwire.com/content/view/20762/1090/](http://www.itwire.com/content/view/20762/1090/)

Its here

---

### Post by bash on 2008-10-23
This only bit that talks about DVD, HD-DVD or Blu-Ray playback is the small part about PowerDVD Linux. Which is still the old, hideous, badly ported version that also does not offer any support for either of the HD formats. So I fail to see "it is here".

---

### Post by mister_pink on 2008-10-23
> **sethvath said:**
> [http://www.itwire.com/content/view/20762/1090/](http://www.itwire.com/content/view/20762/1090/)

Its here
You can tell that article is utter rubbish by the fact that the author doesn't seem to know the difference between "free", "free" and commericial software. Ubuntu is still both "free" and "free", but it is also sponsored by a commercial company that want to make money out of it. The three words are not mutually exclusive.

---

### Post by sethvath on 2008-10-23
With regards to HDDVD, because there is absolutely no red tape and DRM to overcome for any commercial company to implement it on any non vista systems. 

[http://forums.macnn.com/90/mac-os-x/351573/no-blu-ray-hd-dvd-playback/](http://forums.macnn.com/90/mac-os-x/351573/no-blu-ray-hd-dvd-playback/)

> It's also not there for DRM reasons. In order to get an AACS license for an official player, Apple would have to give us a M$ Vista, with everything locked down to prevent users from tampering with the kernel or any stage of the playback. Along with monitoring for tampering, driver registrations encouraged, and mandatory signing of kernel extensions with Apple in order for them to be loaded. Possible callback behavior to let Apple know if some Mac owner is trying to get into the system.

The open source playback utilities are getting close to HDDVD/BRD playback. Within another year, I expect we'll be able to play movies using Mplayer & VLC. Hopefully on less expensive drives, currently the cheapest high definition drive is the XBOX addon for $180 from Amazon.

I really hope Apple *didn't* obtain a license, lock everything down, and put official HD playback into Leopard.

Did you click through the 3 links in the article referring to the codecs for purchase via canonical shop? Apparently not. 
[http://blog.canonical.com/?p=37](http://blog.canonical.com/?p=37)
[https://shop.canonical.com/index.php?cPath=19](https://shop.canonical.com/index.php?cPath=19)
[http://ostatic.com/173388-blog/canonical-opens-codec-sales-and-potential-can-of-worms#rss](http://ostatic.com/173388-blog/canonical-opens-codec-sales-and-potential-can-of-worms#rss)

If you did you would see that [Cyberlink PowerDVD]("http://shop.canonical.com/product_info.php?products_id=243&osCsid=2c9903d6b64ee66513fd5694f12d5c00") != Corel LinDVD

---

### Post by sethvath on 2008-10-23
> **mister_pink said:**
> You can tell that article is utter rubbish by the fact that the author doesn't seem to know the difference between "free", "free" and commericial software. Ubuntu is still both "free" and "free", but it is also sponsored by a commercial company that want to make money out of it. The three words are not mutually exclusive.

I'm certainly not in agreement with the author's biased opinionated post but do no deviate from why I posted the link to inform the OP of the topic at hand. Whether the author is right or wrong no one knows for sure. 

Kindly point me where the 3 "free" statements you list are used in the author's context. I've read the article 3 times and do not see your point.

---

### Post by bash on 2008-10-23
> **sethvath said:**
> If you did you would see that [Cyberlink PowerDVD]("http://shop.canonical.com/product_info.php?products_id=243&osCsid=2c9903d6b64ee66513fd5694f12d5c00") != Corel LinDVD

Meant to say PowerDVD Linux instead of LinDVD. Corrected the mistake. But it still stands that both program are just cheap ports of their windows version. No proper GTK/Qt interface or using recent Linux technologies. Or even support for Blu-Ray(/HD-DVD).

---

### Post by sethvath on 2008-10-23
> **bash said:**
> Meant to say PowerDVD Linux instead of LinDVD. Corrected the mistake. But it still stands that both program are just cheap ports of their windows version. No proper GTK/Qt interface or using recent Linux technologies. Or even support for Blu-Ray(/HD-DVD).

I knew you would go back to the Blue-ray/HD DVD issue

> The AACS 'Digital Rights Management' system in most HD-DVD and all Blu-Ray discs attempts to stop consumers from exercising fair use rights, including:

    * Playing purchased Blu-Ray and HD DVD films using Open Source software.
    * Playing films using standard digital (DVI) or analog (VGA) cables and monitors, which generally do not support HDCP DRM, without a 75% reduction in resolution.
    * Fast forwarding or skipping advertisements.
    * Playing imported films, including when local equivalents may be overpriced or not available. 

Blu-Ray or HD DVD player applications require their unique player (or 'device') key to play discs. These keys are issued by AACS-LA to approved manufacturers that implement the restrictions above. This player key can decrypt each film's volume key, which in turn can decrypt the film's content to play it. 

quote [https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

If it was that easy to implement both natively in linux and mac, no one should be calling for a commercial solution to be done. Should be easy pickings for Cyberlink or any other company to provide a solution ages ago.

---

### Post by unoodles on 2008-10-23
I don't think this is a good idea. I find no point in switching to Linux if you have proprietary software of any kind. (including flash player, drivers, etc..) What I hope happens in the long term?
Proprietary DRM infested formats are cracked and used so widely (after Linux gets about ~25% market share. Then the companies that rule see the light and start switching to open formats.
(yes I know I am dreaming)

---

### Post by semitone36 on 2008-10-23
09 f9 11 02 9d 74 e3 5b d8 41 56 c5 63 56 88 c0 

Never forget.

---

### Post by bruce89 on 2008-10-23
> **bash said:**
> No proper GTK/Qt interface or using recent Linux technologies.

If they did use one of these, the other camp would be annoyed. At least using GTK+ 1.0 annoys everyone.

Mindful of people correcting QT to Qt, I'll say that GTK+ has a '+' on the end.

---

### Post by hardyn on 2008-10-23
if the free codecs are still made available, with the usage warnings, i have no issue with is at all.  if one wishes to adhere to the letter of the law, the paying of licence fees is the only real way to do this.  Those that wish to take the law into their own hands and use the free codecs do so at their own discression.

sounds fair to me.

---

### Post by bash on 2008-10-23
> **sethvath said:**
> I knew you would go back to the Blue-ray/HD DVD issue



quote [https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

If it was that easy to implement both natively in linux and mac, no one should be calling for a commercial solution to be done. Should be easy pickings for Cyberlink or any other company to provide a solution ages ago.

Cyberlink provides Blu-Ray playback solutions for Windows (Vista & **XP**). So I don't see why it can't be done for Linux. (As for Macs: Apple doesn't even offer a Blu-Ray drive yet, so of course they don't care about Blu-Ray playback support). Oh and if you read my post I complained about a lot more than just missing BD/HD-DVD support in PowerDVD Linux. 


> **bruce89]If they did use one of these, the other camp would be annoyed. At least using GTK+ 1.0 annoys everyone.[/quote]

As I said in my first post such an "ideal" software would have both a front-end in Qt and in GTK+

[quote=bruce89]Mindful of people correcting QT to Qt, I'll say that GTK+ has a '+' on the end.[/quote]

I wrote GTK+ in the first post. Just to lazy to always add the plus  said:**
> if the free codecs are still made available, with the usage warnings, i have no issue with is at all. if one wishes to adhere to the letter of the law, the paying of licence fees is the only real way to do this. Those that wish to take the law into their own hands and use the free codecs do so at their own discression.

sounds fair to me.

That is why I wish there would be such a program. Those that wish to stay legal could buy it, the rest could still happily be unlawful (in the countries where it is) and use the cracked versions.

---

### Post by sethvath on 2008-10-23
> **bash said:**
> Cyberlink provides Blu-Ray playback solutions for Windows (Vista & **XP**). So I don't see why it can't be done for Linux. (As for Macs: Apple doesn't even offer a Blu-Ray drive yet, so of course they don't care about Blu-Ray playback support). Oh and if you read my post I complained about a lot more than just missing BD/HD-DVD support in PowerDVD Linux. 


Did you honestly read any of the links I posted? I didnt link them just for show. 

> **The Advanced Access Content System (AACS)** is a standard for content distribution and digital rights management, intended to restrict access to and copying of the next generation of optical discs and DVDs. The specification was publicly released in April 2005 and the standard has been adopted as the access restriction scheme for HD DVD and Blu-ray Disc (BD). It is developed by AACS Licensing Administrator, LLC (AACS LA), a consortium that includes Disney, Intel, **Microsoft**, Matsushita (Panasonic), Warner Bros., IBM, Toshiba and Sony.


You see the correlation why Microsoft supports the format playback and yet none of the Linux distributions and/or linux related software company is on board BESIDES the fact that windows control over 80% of the pc market?

To understand the different agreements you HAVE TO COMPLY with AACS
[http://www.aacsla.com/support/](http://www.aacsla.com/support/)

---

### Post by bash on 2008-10-23
You linked to pages talking about Canonical selling Fluendo codecs. Again fail to see how that has anything to with DVD, Blu-Ray or HD-DVD playback support on Linux. And you link to a page explaining how to illegally get access to HD-DVDs. Again this has nothing to do with lawful playback of DVDs, Blu-Ray dics or HD-DVDs on linux.

If Cyberlink can release a piece of software that offers legal playback of HD media on Windows XP (which has none of the tied down DRM settings of Vista) I fail to see why it is not possible for them release a proper version for Linux systems that offers all the playback plus a useable interface (in GTK+ and/or Qt).

Oh and on the topic of Microsoft being part of consortium that passed the specification. Again if I (or anyone else) install PowerDVD 8 on Windows XP I receive legal playback capability through the buying of a product from Cyberlink. Nowhere do I there interact with Microsoft (Besides that in consortium are also companies like Intel & IBM which the last time I checked support Linux quite heavily). 

So please could you finally show me an argument that clearly states why legal Blu-Ray support is not possible or stop saying that you can't have legal playback of Blu-Rays on Linux.

---

### Post by sethvath on 2008-10-23
The link with Canonical selling Fluendo codecs contains the link to the Canonical shop selling Cyberlink PowerDVD Linux which is what you mistakenly referred LinDVD as was it not? Does Cyberlink PowerDVD not play restricted DVD formats or must I hand hold you to see every point I'm trying to make because apparently we're from different planets. 

Please quote the statement where I explicitly said "why legal Blu-Ray support is not possible or stop saying that you can have legal playback of Blu-Rays on Linux."

Do not twist my words unless you are able to follow up with it. I could play schematics with you all day if you wish but that is hardly the point of the topic. This silly "argument" is going no where.

---

### Post by bash on 2008-10-23
I agree. We are going in circles here. I made a topic that I wished there would be a program offering DVD, Blu-Ray and HD-DVD playback legally, with a nice and snappy interface in GTK+ or Qt.

You said that "it's here". Which it isn't. Then you said Blu-Ray playback is just not possible. Which you so far haven't backed up with no argument or proof. So I'm starting to wonder if you are not just trolling around, because everytime I ask something or question your argument, you just bring up a new point or different point that does nothing to answer the question. Best example:

[quote=bash]So please could you finally show me an argument that clearly states why legal Blu-Ray support is not possible or stop saying that you can't have legal playback of Blu-Rays on Linux.[/quote]

Your response:

[quote=sethvath]Please quote the statement where I explicitly said "why legal Blu-Ray support is not possible or stop saying that you can have legal playback of Blu-Rays on Linux."[/quote]

Did you actually read what I wrote? Anyways as this has no point to it I'll stop replying to you now. If any other people feel like contributing something though, I'll feel happy to reply to them.

---

### Post by Mr. Picklesworth on 2008-10-23
Relying on a single multimedia framework *works* here because that single framework is not evil. The user is not limited in what he can put in there, and codecs exist for practically everything. (Contrary to Quicktime, for example, which won't handle mpeg2s without an extra $20). It can even deal with [iTunes stuff]("http://www.el-tunes.com/") now!

The article Sethvath links to is astoundingly terrible. That guy spent 3 pages convincing me that he has absolutely no clue what free software is. What a joke.

Having said that, three other nice media programs shaping up well:
-Boxee (astounding piece of work!).
-Canola. Crossing my fingers on that one; it's currently only targeting Nokia's Internet Tablets, but it is really good.
-Entertainer.

MythBuntu of late looks really good.

Some great stuff is emerging from the madness.

As for a commercial media player, I don't think that's necessary. Tying codecs to a media player is a recipe for disaster. I have a working media player as it is, but I would like GStreamer to support everything. This way, I can install the codec and then every program on my desktop, by it Rhythmbox, Totem, Jokosher or even a video converter will support that format seamlessly.

---

### Post by stmiller on 2008-10-23
Somewhat related, Nero has bluray burning on Linux. [[link]("http://www.nero.com/enu/linux3.html")]

Blu Ray playback from a major vendor will come soon, I'm sure.

---

### Post by bash on 2008-10-23
> **stmiller said:**
> Somewhat related, Nero has bluray burning on Linux. [[link]("http://www.nero.com/enu/linux3.html")]

Blu Ray playback from a major vendor will come soon, I'm sure.

Yep, Nero is a good example of how to create a good commercial Linux Application. It uses Linux technologies, has a native Linux interface and is still simple and easy to use (not like the latest Windows version of Nero, that sadly get more and more bloated with each release).

[quote=Mr. Picklesworth]Relying on a single multimedia framework works here because that single framework is not evil. The user is not limited in what he can put in there, and codecs exist for practically everything. (Contrary to Quicktime, for example, which won't handle mpeg2s without an extra $20). It can even deal with iTunes stuff now!

The article Sethvath links to is astoundingly terrible. That guy spent 3 pages convincing me that he has absolutely no clue what free software is. What a joke.

Having said that, three other nice media programs shaping up well:
-Boxee (astounding piece of work!).
-Canola. Crossing my fingers on that one; it's currently only targeting Nokia's Internet Tablets, but it is really good.
-Entertainer.

MythBuntu of late looks really good.

Some great stuff is emerging from the madness.

As for a commercial media player, I don't think that's necessary. Tying codecs to a media player is a recipe for disaster. I have a working media player as it is, but I would like GStreamer to support everything. This way, I can install the codec and then every program on my desktop, by it Rhythmbox, Totem, Jokosher or even a video converter will support that format seamlessly.[/quote]

I agree with you for the "normal" media playback such as video and audio playback. Me for example, I am happy with the combination of mplayer/vlc for video and Banshee for audio. But sadly this does not offer me a legal way to playback my DVDs or even Blu-Ray movies. Nor seems there to be a legal way to implement those features into my favourite open-source players in the near future. That is exactly why I would prefer at, least for now, a application that is a proper Linux program (like Nero Linux), that gives me the chance to play my DVDs and HD medias. I do know I could crack it, but I am explicitly talking about a legal option. And sadly the only thing we have so far, are two commercial players (are there any more I might have missed?) that only support DVDs (no HD media) and that look hideous and out of place on Linux systems.

---

### Post by Polygon on 2008-10-23
> **semitone36 said:**
> 09 f9 11 02 9d 74 e3 5b d8 41 56 c5 63 56 88 c0 

Never forget.

too bad that key does not work anymore. They made it so they can change the key just in case stuff like that happened.

Anyway, just wait for someone to release a library that will play bluray, then it will get included in programs like VLC and we will be on our merry way. No need for a commercial media player which will most likely suck

---

### Post by mrgnash on 2008-10-24
> **Polygon said:**
> too bad that key does not work anymore. They made it so they can change the key just in case stuff like that happened.

Anyway, just wait for someone to release a library that will play bluray, then it will get included in programs like VLC and we will be on our merry way. No need for a commercial media player which will most likely suck

Exactly right. There will be new keys, new ways of getting around the DRM bs imposed on the technology. No need to fret -- not that I am anyway, because I don't give a damn about playing back optical media... it's a hassle.

---

