---
title: "Ubuntu torrents sabotaged?"
date: 2010-05-02
forum: The Cafe
---

### Post by DawieS on 2010-05-02
I have had the unfortunate experience of being targeted by spammers while attempting to download the Lucid Beta2 and Lucid Final Release versions with Transmission BitTorrent. I have wasted about 2.6 GB of bandwidth and ended up with about 450 MB worth of incomplete verified material split up between the 2 torrents.

What happens is that the torrents start up normally and run at full speed, both down- and uploading. After about an hour, the 'verified' number starts slowing down and eventually comes to standstill, while the 'downloaded' number still increase at full speed.

I regularly use torrents, and have never experienced something similar with other torrents. I eventually gave up on both these torrents, after a lot of testing and restarting with different options.

What is interesting, is that the Beta2 torrent reported nothing as corrupt, and the Final Release torrent reported only 2 MB as corrupt. This implies that the balance of about 2.15 GB downloaded must have been duplicates of what my torrent client already had.

The wasted bandwidth did not really cost me anything, since I have an 'uncapped' ISP account which became available locally recently. It is 'uncapped', as long as you don't use more than 20 GB per month, in which case you are throttled so heavily that even normal browsing becomes a nightmare! Also downloading with torrents is only possible at night, since during daytime it is throttled to <1 KB/s.

The only bunch I can think of with sufficient motive (and money) to do this sort of thing, is Mr. Gates and his clowns.

I have done a quick search through the forums, and did not find other similar reports. It seems a bit strange that I am the only one with this problem...](*,)

---

### Post by Viva on 2010-05-02
Are you downloading on windows? I had a similar problem a few releases back that was caused by disk fragmentation on windows. I moved the iso to an ext3 partition, resumed it on linux and it finished quickly.

---

### Post by 3rdalbum on 2010-05-02
I have had this problem on other torrents.

---

### Post by ikt on 2010-05-02
> **DawieS said:**
> It is 'uncapped', as long as you don't use more than 20 GB per month

Yeah we have that in Australia, nobody refers to it as uncapped because quite clearly it isn't :P


> The only bunch I can think of with sufficient motive (and money) to do this sort of thing, is Mr. Gates and his clowns.

It's an unfortunate human limitation that our brains have not evolved further in such a way that we rely on junk conspiracy theories over the rationalisation of no theory or 'I don't know'.

You didn't mention what torrent client you are using but the issue you had is very common, I've had several torrents in the past download well over the amount needed.

Utorrent has an faq on it:

> What does Wasted and hashfails mean?

Wasted shows a combination of discarded data and bad data. Discarded data is data that's sent to you by a peer that your client didn't want. Hashfails happen when bad data is received and the client throws it out.

More than likely a peer close to you is sending out a corrupt iso, most clients will ignore them after several hashfails.

---

### Post by cchhrriiss121212 on 2010-05-02
I had this problem downloading the 10.04 final release using transmission, checking under properties showed that I had downloaded 3GB for the 700MB image. I doubt it is sabotage as I have seen it when downloading other linux OS's using torrents, but I would like to know why it happens as my connection is only 0.5Mbs.

---

### Post by DawieS on 2010-05-02
I was downloading using Karmic (Ubuntu 9.10), installed in an ext3 partition. Disk checks are regularly done (every 25 boots I think), and I did not notice any fragmentation, or other disk problems, reported. Available disk space is more than enough as well.

Just last week I downloaded a massive game demo ISO (+- 3 GB) for one of my kids, using Transmission BitTorrent, also without any problems.

After I eventually downloaded Lucid Beta2 via http, I have also updated and customized it to my liking. Subsequently I had requests from family and friends for CD's of the official release of Lucid, so I had to eventually download that via http as well, after another failed torrent attempt.

---

### Post by Lightstar on 2010-05-02
I use Deluge, had no problems at all.

In the past I did have a few "corrupted" data problems, that was when I downloaded something on linux, and decided to continue downloading it on windows (files were on a ntfs drive).  It worked fine 80% of the time.

---

### Post by Giant Speck on 2010-05-02
[IMG]http://i44.tinypic.com/10gfjit.jpg[/IMG]

---

### Post by chriswyatt on 2010-05-02
Damn you Bill Gates! *shakes fist*

---

### Post by clanky on 2010-05-02
Those evil folks at Redmond, what will they stoop to next? :)

---

### Post by Khakilang on 2010-05-02
Its Steve Ballmer's fault.

---

### Post by clanky on 2010-05-02
> **Koh Kook Loon said:**
> Its Steve Ballmer's fault.

Don't forget Bill Gates (and probably Melinda too) that was what they have been  doing with all that money after all, it wasn't being donated to charity they were setting up a secret underground laboratory in a hollowed out volcano to sabotage Ubuntu torrents.

---

### Post by gnomeuser on 2010-05-02
I downloaded 4 ISOs so far (alternate i386, desktop i386+amd64 and the netbook edition). No issues what so ever and they shared 1:1 without any issue.

---

### Post by dfreer on 2010-05-02
> **clanky said:**
> Those evil folks at Redmond, what will they stoop to next? :)

[IMG]http://www.architecturaliron.com/gallery/full%20images/Stoop-1.jpg[/IMG]

---

### Post by P4man on 2010-05-02
Id have a chat with your ISP if I were you. And then get another one.

---

### Post by KiwiNZ on 2010-05-02
> **DawieS said:**
> I have had the unfortunate experience of being targeted by spammers while attempting to download the Lucid Beta2 and Lucid Final Release versions with Transmission BitTorrent. I have wasted about 2.6 GB of bandwidth and ended up with about 450 MB worth of incomplete verified material split up between the 2 torrents.

What happens is that the torrents start up normally and run at full speed, both down- and uploading. After about an hour, the 'verified' number starts slowing down and eventually comes to standstill, while the 'downloaded' number still increase at full speed.

I regularly use torrents, and have never experienced something similar with other torrents. I eventually gave up on both these torrents, after a lot of testing and restarting with different options.

What is interesting, is that the Beta2 torrent reported nothing as corrupt, and the Final Release torrent reported only 2 MB as corrupt. This implies that the balance of about 2.15 GB downloaded must have been duplicates of what my torrent client already had.

The wasted bandwidth did not really cost me anything, since I have an 'uncapped' ISP account which became available locally recently. It is 'uncapped', as long as you don't use more than 20 GB per month, in which case you are throttled so heavily that even normal browsing becomes a nightmare! Also downloading with torrents is only possible at night, since during daytime it is throttled to <1 KB/s.

The only bunch I can think of with sufficient motive (and money) to do this sort of thing, is Mr. Gates and his clowns.

I have done a quick search through the forums, and did not find other similar reports. It seems a bit strange that I am the only one with this problem...](*,)

With respect , it is ridiculous to assume that Microsoft would be involved in sort activity. Thread closed :rolleyes:

---

