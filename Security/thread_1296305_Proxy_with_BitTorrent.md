---
title: "Proxy with BitTorrent"
date: 2009-10-20
forum: Security
---

### Post by flyerbrooks on 2009-10-20
If my FireFox V3.5 web browser is configured to use a proxy will my BitTorrent client automatically follow the same protected path? Also if the proxy suddenly goes offline will the bitTorrent revert to an open path or stop until the proxy is open again. Thanks for any info on this and i am relatively new to Ubuntu Jaunty 9.04
Cheers 
:-k

---

### Post by undecim on 2009-10-20
Firefox proxy settings apply only to firefox. Most bittorrent apps will allow you to specify in the preferences window a proxy to use, and as far as I know, no bittorrent apps will switch to a direct connection if the proxy fails.

Also, by "proxy" I hope you aren't referring to TOR. Its slow for torrenting, and its also considered rude to use torrents with it.

---

### Post by flyerbrooks on 2009-10-20
Thanks undecim, thats the line i was thinking along. Never had any success in getting Tor to work in Linux so far, so just configuring proxies by hand. I agree with you that torrents slow down the Tor network but i read lately that because everybody is doing it there was no other option than to increase capacity. More relays=same/more speed (not that im saying i agree with this) Thanks

---

### Post by witeshark17 on 2009-10-21
Please keep us posted on what you find out. :)

---

### Post by ackanao on 2009-10-21
There are a number of ways to use bittorrent "safely" and none of them includes Tor:

In most cases something like [[COLOR="Red"]MoBlock[/COLOR]]("http://moblock.berlios.de/") or [[COLOR="Red"]iplist[/COLOR]]("http://iplist.sourceforge.net/") will do the trick; If that's not working for you, you can use free VPN solutions like UltraVPN (last time I checked speed was very good) or cheap VPN's (5$/month) like AlonWeb; Then there's [[COLOR="Red"]I2P[/COLOR]]("http://www.i2p2.de/"), [[COLOR="Red"]BitBlinder[/COLOR]]("http://www.bitblinder.com/")...

Useful links:

[[COLOR="Red"]I2P[/COLOR]]("http://en.wikipedia.org/wiki/I2P")
[[COLOR="Red"]Anonymous P2P[/COLOR]]("http://en.wikipedia.org/wiki/Anonymous_P2P")

[[COLOR="Red"]MoBlock Ubuntu documentation[/COLOR]]("https://help.ubuntu.com/community/MoBlock")
[[COLOR="Red"]General MoBlock thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=803183")
[[COLOR="Red"]MoBlock download[/COLOR]]("http://moblock-deb.sourceforge.net/")

[[COLOR="Red"]Iplist[/COLOR]]("http://en.wikipedia.org/wiki/Iplist")
[[COLOR="Red"]Iplist homepage[/COLOR]]("http://iplist.sourceforge.net/")

If you want my opinion, I see no reason for anonymizing bittorrent unless your ISP is throttling the speed or blocking p2p traffic - if that's the case, you have far more better solutions than to abuse Tor network. ;)

---

### Post by flyerbrooks on 2009-10-24
Thanks ackanao
Some useful and interesting reading, much appreciated :) I can see from other postings of yours you are quiet an authority on this subject. Are you still using polipo?

---

### Post by ackanao on 2009-10-24
Oh my, thanks, but I'm far from beeing an authority on this subject beleive me - I'm just a long-time Tor user and I guess quite familiar with it;

There's a plenty of documentation on Tor's homepage (maybe not well organized) and on or-talk mailing list - It's a very interesting read and it will help you to get familiar with Tor.

There is, however, a "condoned" way to use any torrent client with Tor: 

Use Tor to anonymize your communication with torrent-tracker but download torrents as usual (without Tor);

You can protect yourself further by configuring your torrent client to only accept encrypted connections and you can use Moblock or iplist to block "unwanted" IP's.

I've never tried this myself but I know that this metod is "approved" by Tor developers, Tor nodes operators, and all Tor users.

Take a look at this threads on or-talk:

[http://archives.seul.org/or/talk/Jun-2008/msg00168.html]("http://archives.seul.org/or/talk/Jun-2008/msg00168.html")
[http://archives.seul.org/or/talk/Feb-2009/msg00171.html]("http://archives.seul.org/or/talk/Feb-2009/msg00171.html")

and here's the Tor wiki article:
[https://wiki.torproject.org/noreply/TheOnionRouter/TorifyHOWTO/BitTorrent]("https://wiki.torproject.org/noreply/TheOnionRouter/TorifyHOWTO/BitTorrent")

Try for yourself, maybe it'll work for you - if you're not satisfied with the results then checkout some free/cheep VPN solutions (just search google you'll find plenty of them).

I still use polipo - never did any benchmark tests but it looks like it's faster than Privoxy; polipo does not have such a filtering capabilities like Privoxy but I don't mind that at all: Whether I use Tor or not, I always browse the internet with cookies, Java, Javascript, Flash (and all other plugins) disabled; I use hosts file and couple of security/privacy related add-ons for Firefox so most of the web-annoyances are already filtered anyway.

---

