---
title: "Everyone quit downloading the beta for a few..."
date: 2009-10-02
forum: The Cafe
---

### Post by lykwydchykyn on 2009-10-02
I need to do some updates, and it's taking forever! :P

Seriously, it's been like a release day today, must be a ton of interest in Karmic.

---

### Post by ElSlunko on 2009-10-02
Took me a good 15 minutes just to grab the .torrent! Holy moly.

---

### Post by toupeiro on 2009-10-02
mirrors mirrors mirrors!

---

### Post by ikt on 2009-10-02
> **toupeiro said:**
> mirrors mirrors mirrors!

torrents torrents torrents?

I don't understand why more people don't use the torrent system to actually download 'linux iso's' :P

---

### Post by toupeiro on 2009-10-02
> **ikt said:**
> torrents torrents torrents?

I don't understand why more people don't use the torrent system to actually download 'linux iso's' :P

Because some ISP's QoS torrents (Mine doesn't but some do), and I run databases I'd rather not take down for the upgrade process.

---

### Post by ikt on 2009-10-02
> **toupeiro said:**
> Because some ISP's QoS torrents.

Enable encryption?

> As of January 2005, BitTorrent traffic made up more than a third of total internet traffic.[2] Some ISPs deal with this traffic by increasing their capacity whilst others use specialised systems to throttle (i.e. slow down) peer-to-peer traffic. Obfuscation and encryption make traffic harder to detect and therefore harder to throttle. These systems are not designed to provide anonymity or confidentiality.

[http://en.wikipedia.org/wiki/BitTorrent_protocol_encryption](http://en.wikipedia.org/wiki/BitTorrent_protocol_encryption)

> and I run databases I'd rather not take down for the upgrade process.

what kind of databases on an unstable system? just wondering, I've never heard someone say that before.

---

### Post by lykwydchykyn on 2009-10-02
> **ikt said:**
> torrents torrents torrents?

I don't understand why more people don't use the torrent system to actually download 'linux iso's' :P

I can never get them to work.  Probably the firewall at work.

---

### Post by toupeiro on 2009-10-02
> **ikt said:**
> Enable encryption?



[http://en.wikipedia.org/wiki/BitTorrent_protocol_encryption](http://en.wikipedia.org/wiki/BitTorrent_protocol_encryption)

my god, yes, you're insight will thwart QoS the world around... ](*,)


Not only does encryption slow things down, not only does encryption have to be decryptable (enabled) on ALL ends, but your packet header is still going to tell your ISP what you're doing. which means you have encryption overhead AND you're potentially fighting QoS.  2005 was a long friggin time ago in the world of networking.

Look, if you want to use torrents fine, but you asked why some people don't.  I gave you a reason.

...  And don't presume that because I'm running alpha or beta that my system is unstable.

---

### Post by ikt on 2009-10-02
> **toupeiro said:**
> Not only does encryption slow things down, not only does encryption have to be decryptable on ALL ends, but your packet header is still going to tell your ISP what you're doing.

I don't think you understand what encryption on torrents does.. either that or you saw 'encryption' and ignored the rest of my post.

---

### Post by toupeiro on 2009-10-02
> **ikt said:**
> I don't think you understand what encryption on torrents does.. either that or you saw 'encryption' and ignored the rest of my post.

I saw the rest of your post.  I've worked with QoS since 2005 and I know for a fact I can throttle torrents, encryption or not.

Making something harder != making it impossible, by any means.

---

### Post by HappyFeet on 2009-10-02
> **toupeiro said:**
> 
Not only does encryption slow things down

Really? I use encryption and have to throttle it back, because it will use all of my bandwidth if I don't. Where do you get your info anyway?

---

### Post by toupeiro on 2009-10-02
> **HappyFeet said:**
> Really? I use encryption and have to throttle it back, because it will use all of my bandwidth if I don't. Where do you get your info anyway?

Torrents, by nature, can use all of your bandwidth if you aren't throttling.  Encryption doesn't make that possible.  I get my information from working with Cisco and HP switches and routers in the last 5 years, understanding the [OSI model]("http://en.wikipedia.org/wiki/OSI_model"), and using torrents for quite some time myself.  In my own testing on my current ISP and other ISPs in the past, which did not use QoS for torrents so it appears, I have been able to saturate my bandwidth as well.  This is also .. something I do not want to do.   I could throttle it.. or, I could use a mirror.  Requiring encrypted transports also cuts the number of connections you will be able to use because you will be denying anyone that is doing so unencrypted. Look, my god, I didn't say torrents suck, I said **there are valid reasons people don't use them**

Encryption is only going to speed things up if its successful in bypassing a QoS rule, but if you are using encryption without QoS, then you're potentially adding more layer-4 traffic than you need, which is the layer Bit torrent is doing encryption (TLS).

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-02
I can't even apt-get update and  I need to get a few fixes

---

### Post by HappyFeet on 2009-10-02
> **&#1057 said:**
> I can't even apt-get update and  I need to get a few fixes

You'll just have to wait until the initial rush dies down.

---

### Post by Firestem4 on 2009-10-02
> **lykwydchykyn said:**
> **I**** need to do some updates, and it's taking forever! :P**

Seriously, it's been like a release day today, must be a ton of interest in Karmic.

Oh...so thats why i'm getting 20k/s, lol.

---

### Post by hoppipolla on 2009-10-02
> **lykwydchykyn said:**
> I need to do some updates, and it's taking forever! :P

Seriously, it's been like a release day today, must be a ton of interest in Karmic.

haha that made me smile :)

Yeah I grabbed the beta too :)

Lovin' it!

---

### Post by lovinglinux on 2009-10-02
> **toupeiro said:**
> Requiring encrypted transports also cuts the number of connections you will be able to use because you will be denying anyone that is doing so unencrypted.

Yes, that's true. But most people use encryption these days, so unless you are on a very small swarm, it is unlikely that encryption will have a detrimental effect on your torrent download speeds.

For those interested on BitTorrent take a look at the thread [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

EDIT: it seems that the tracker issue has been fixed and I'm downloading it right now, with very good speed. It almost using all my bandwidth. BTW,  I use full encryption, Deluge blocklist and moblock :)

---

### Post by oldsoundguy on 2009-10-02
Even the repositories were hung up this AM .. most centering around the Samba update (took three times to get it FINALLY .. and on FOUR manchines!) and the boatload of stuff for Open Office.

---

### Post by ikt on 2009-10-02
> **lovinglinux said:**
> Deluge blocklist and moblock :)

blocklist is definitely useless, and now I'm wishing I had bookmarked a site which showed that it blocked <2% of all the ip's that media defender was using to get people.

Here it is:

> The 'Paranoid' eMule IP filter was retrieved on September 27, 2007. The Level1 IP blacklist, which is supposed to block all known anti-p2p IPs, was retrieved on September 30, 2007.

> The total number of IPs used by Media Defender starting with 116 was 1,474. Obviously, BlueTack did block all IPs that started with 116, but how many Media Defender IPs were successfully blocked? When Slyck investigated, there was a common theme that blocklists seemingly jumped over several ranges used by Media Defender. After some extensive study using the Level1 list for anti-p2p companies and the 'Paranoid' list, BlueTack would have successfully blocked 16 IPs. Thus, this sample test offered 1.09% protection against Media Defender in that range. 

[http://slyck.com/forums/viewtopic.php?t=38295](http://slyck.com/forums/viewtopic.php?t=38295)

---

### Post by lovinglinux on 2009-10-02
> **ikt said:**
> blocklist is definitely useless, and now I'm wishing I had bookmarked a site which showed that it blocked <2% of all the ip's that media defender was using to get people.

There are a lot of controversy if the IP filters are effective or not and that depends on who you want to block and which IP ranges you are using. Anyway, this is not the point of discussion. I was simply pointing that even with full encryption and IP blocking, I'm still able to download Ubuntu torrents with maximum speed.

I'm just trying to say that In cases like this one, when the repositories servers are overwhelmed, the best option is to use BitTorrent. You can get excellent download speeds even if you use encryption and IP blocklists.

BTW, my download is already finished and I'm seeding it. When I tried to download Karmic yesterday via http the download speed was 20Kb/s. I have downloaded using BitTorrent at 450 KiB/s, which is almost my download bandwidth limit.

---

### Post by toupeiro on 2009-10-02
> **lovinglinux said:**
> There are a lot of controversy if the IP filters are effective or not and that depends on who you want to block and which IP ranges you are using. Anyway, this is not the point of discussion. I was simply pointing that even with full encryption and IP blocking, I'm still able to download Ubuntu torrents with maximum speed.

I'm just trying to say that In cases like this one, when the repositories servers are overwhelmed, the best option is to use BitTorrent. You can get excellent download speeds even if you use encryption and IP blocklists.

BTW, my download is already finished and I'm seeding it. When I tried to download Karmic yesterday via http the download speed was 20Kb/s. I have downloaded using BitTorrent at 450 KiB/s, which is almost my download bandwidth limit.

I'm pulling off of the easynews mirror at almost 1 MiB/sec...  As I've tried to explain, Torrents aren't always faster than completely untouched mirrors, and there is still plenty of validity in using mirrors.  Most people probably don't know where to even select a mirror versus a main server, and have never tried.  I'd hope those people would consider this a chance to learn something new, but they'd rather lecture people for not doing things their way. :P  Yes, I am generalising.

---

