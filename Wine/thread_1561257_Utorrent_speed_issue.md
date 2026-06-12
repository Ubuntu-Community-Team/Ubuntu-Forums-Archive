---
title: "Utorrent speed issue"
date: 2010-08-26
forum: Wine
---

### Post by primetime34 on 2010-08-26
I have to run utorrent for some of my torrents because transmission doesn't handle udp trackers.
So I have the latest version of utorrent running through wine, but my upload is not working at all.  My port is forwarded and utorrent is recognnizing that.  When I try and run the setup guide, I cannot connect to the server to see how fast my upload and download should be.

What is going on?  Is there some special setting I need to be aware of?  I'm running lucid.  Thanks.

---

### Post by v1ad on 2010-08-26
try qbittorrent.
```

sudo apt-get install qbittorrent

```

supports magnets and should be what you are looking for. running anything through wine is inefficient.

---

### Post by primetime34 on 2010-08-26
> **v1ad said:**
> try qbittorrent.
```

sudo apt-get install qbittorrent

```supports magnets and should be what you are looking for. running anything through wine is inefficient.

Wow qtorrent looks great and I might replace my use of transmission with qtorrent (especially with labels!!).  However, I have one torrent whose tracker won't accept qtorrent.  They only accept utorrent and some other windows options.  So while I really appreciate the suggestion, I do need some help with utorrent.  Thanks.

---

### Post by JBAlaska on 2010-08-26
If by "support udp" you mean DHT, I don't think qtorrent supports it.


Check out Deluge, It's a much more powerful BT client. Also checkout the Blocklist plug-in in Deluge, it works great.

---

### Post by Dayofswords on 2010-08-26
Deluge is awesome, except it works alot better on linux that windows, fine with that though

---

### Post by 0004tom on 2010-08-26
> **primetime34 said:**
> When I try and run the setup guide, I cannot connect to the server to see how fast my upload and download should be.

What server are you trying to connect to? If you want a speedtest i suggest you use speedtest.net in your browser (you'll need flash) that will give you a rough idea how fast your connection is.

---

### Post by primetime34 on 2010-08-26
I appreciate the suggestions for the other bittorrent clients.  However, I need to get utorrent working for this particular tracker.

As far as speed goes, my torrents run just fine in transmission.  When I try to run any torrent through utorrent, the speeds are significantly slower and the upload is almost non-existent.  For example, I used the ubuntu torrent in utorrent.  In transmission it downloads at my cap (450 kB/s) and uploads at my cap (75 kB/s).  However, the same torrent in utorrent only runs at 60 kB/s and uploads at 1 kB/s.  Any thoughts on why?

---

### Post by v1ad on 2010-08-27
thats the first time i heard of a tracker being picky about what torrenter uses it. i have a feeling that you are doing something wrong. deluge or qbittorrent support everything.

---

### Post by v1ad on 2010-08-28
qbittorrent has a feature that identifies itself as utorrent btw. look in preferences

---

### Post by cwwilson721 on 2010-08-29
> **v1ad said:**
> qbittorrent has a feature that identifies itself as utorrent btw. look in preferencesThere are SOME trackers that only like certain clients. That's life on the web...

You can select MANY different torrent clients in qbittorrent to avoid "blacklisting", like:

[LIST]
[*]utorrent (Even can change build numbers!)
[*]Vuze (Yep. The tracker thinks you're a Windows Nut)
[*]ktorrent (The KDE bittorent client)
[*]qbittorent
[/LIST]
It is accessed thru Tools > Preferences > bittorrent (Should be a setting saying something about "Whitelist"

I gave up on any other client (At least in the GUI. I use another client in cli). qbittorent is fast, configurable, and works GREAT with my proxy server (It can use either HTTP or SOCKS4/5, or any combo you want). Plu8s, it has a remarkably small footprint for what it does (Vuze is such a huge resource hog...)

---

