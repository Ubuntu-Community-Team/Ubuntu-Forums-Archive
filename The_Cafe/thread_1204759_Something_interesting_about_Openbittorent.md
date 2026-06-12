---
title: "Something interesting about Openbittorent"
date: 2009-07-05
forum: The Cafe
---

### Post by monsterstack on 2009-07-05
[SIZE="1"]I just posted this on my [blag]("http://bambambambam.wordpress.com/2009/07/05/the-pirate-bay-and-now-something-completely-different/"), but nobody reads that and I figured more people should know about this, so I'll repost here.[/SIZE]

I&#8217;ve seen an awful lot of folk throwing all of their toys out of the pram in light of the news that the Pirate Bay is to be sold to some shady company who wish to monetise it. Botnets have been summoned to take down the Pirate Bay&#8217;s homepage, and many people appear to have shredded their teeshirts in protest. All this meant that the news of a new bittorrent tracker passed by with rather muted coverage in the press; in fact I would add a link to that muted reception, but I can&#8217;t find any.

The service is called OpenBittorrent and as a simple tracker, it is not bound to any particular site, which effectively adds an extra layer of abstraction and decentralisation for filesharing networks. Will they eventually get shut down, too? It seems unlikely, for now. As the project&#8217;s homepage explains:

>     Just to make it clear so people sending DMCA takedown notices understand:

[LIST]
[*]We do not have any content.
[*]We are not a bittorrent site, we are just a tracker, we can not see what content is behind an info_hash.
[*]We don&#8217;t have any torrent files.
[*]We can&#8217;t give you any IP addresses in any other way than normal tracker usage &#8211; the software don&#8217;t support it.
[*]We can&#8217;t verify any claims when we have no data other than the info_hash.
[*]We can&#8217;t block info_hash keys from being registered with the tracker.
[*]We don&#8217;t have any logs or ways to trace previous connections, there is just not enough disk and IO resources in the world for that (at least not at our operational budget).
[*]And most importantly, we have no time.
[/LIST]

Seems like a good idea. So how about the Pirate Bay? What do they have to do with any of this?

```
ryan@lappy:~$ host openbittorrent.com 
openbittorrent.com has address 212.63.222.20
openbittorrent.com mail is handled by 10 ap.tfr.org.
ryan@lappy:~$ host 212.63.222.20
20.222.63.212.in-addr.arpa domain name pointer tfr.org.
ryan@lappy:~$ host tfr.org
...
**Registrant Name:[Fredrik Neij]("http://en.wikipedia.org/wiki/Fredrik_Neij")**
...
```

:grin:

---

### Post by Bigtime_Scrub on 2009-07-05
I dont get it. How are you supposed to use this "open bittorrent?"

I use demonoid anyway but having another torrent site would be nice. There is always isohunt.

---

### Post by monsterstack on 2009-07-05
> **Bigtime_Scrub said:**
> I dont get it. How are you supposed to use this "open bittorrent?"

I use demonoid anyway but having another torrent site would be nice. There is always isohunt.

When people create torrent files and upload them to torrent sites, they must include a tracker. Many bittorrent sites act as both an indexer of torrent files, and as tracker services. The tracker is a tool to control the communication between computers in the network. It's the tool that allows users to see how many seeders and leechers there are. In fact, a lot of sites simply use the Pirate Bay's tracker, yet index their own torrent files. Even if the torrent files are deleted, downloads won't stop all of a sudden, because the tracker is still running. The idea is to encourage people to include this new tracker on every torrent file they make. This means that *wherever* the torrent file is posted, the open tracker will know about it.

The entirety of the Pirate Bay's torrent files can be stored on a USB stick. If and when the site gets completely shut down, all someone has to do is upload these torrents somewhere else. That won't be very difficult to do. It means file-sharing will continue for a very long time.

---

### Post by Gias Kay on 2009-07-06
[http://torrentfreak.com/openbittorrent-tracker-muscles-in-on-the-old-pirate-bay-090705/](http://torrentfreak.com/openbittorrent-tracker-muscles-in-on-the-old-pirate-bay-090705/)

---

