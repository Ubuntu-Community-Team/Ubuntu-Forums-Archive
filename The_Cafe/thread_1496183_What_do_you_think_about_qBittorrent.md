---
title: "What do you think about qBittorrent?"
date: 2010-05-29
forum: The Cafe
---

### Post by lovinglinux on 2010-05-29
I have already used uTorrent, Azureus, Transmission, Deluge, Ktorrent and others. Deluge was my preferred client for a long time, but I switched to KDE when Karmic was released and started to Ktorrent, which I loved. But since KDE 4.4, I feel that Ktorrent is getting a little bloated for my taste and I didn't like some aspects of the  new interface. So today I decided to try another client and installed qBittorrent. 

I'm really amazed. The interface is really simple and functional (looks like uTorrent), it has all the features I need and the speed is really fast. I was able to reach maximum speed in a couple of minutes and it is has been steady since then. Considering I'm downloading a torrent with a lot more peers than seeders, this is really impressive

So far it looks like this will be my default client from now on.

What do think about qBittorrent? Please specify pros and cons.

---

### Post by Chronon on 2010-05-29
I don't have too much experience with it yet, but it seems to cover the bases I need and certainly runs lighter than Ktorrent (which I still like).  I will have to use it a bit more to get a complete impression of it, though.

---

### Post by lovinglinux on 2010-05-29
> **Chronon said:**
> I don't have too much experience with it yet, but it seems to cover the bases I need and certainly runs lighter than Ktorrent (which I still like).  I will have to use it a bit more to get a complete impression of it, though.

I'm experiencing some issues with it's UPnP feature and it doesn't seem to delete the .torrents after loading them. Besides that, looks great. It is really fast. Perhaps the fastest torrent client I ever used. It is maxing out all torrents I start in a couple of minutes and keeping the speed at the top through the entire download. I'm really impressed.

---

### Post by Shining Arcanine on 2010-05-29
> **lovinglinux said:**
> I have already used uTorrent, Azureus, Transmission, Deluge, Ktorrent and others. Deluge was my preferred client for a long time, but I switched to KDE when Karmic was released and started to Ktorrent, which I loved. But since KDE 4.4, I feel that Ktorrent is getting a little bloated for my taste and I didn't like some aspects of the  new interface. So today I decided to try another client and installed qBittorrent. 

I'm really amazed. The interface is really simple and functional (looks like uTorrent), it has all the features I need and the speed is really fast. I was able to reach maximum speed in a couple of minutes and it is has been steady since then. Considering I'm downloading a torrent with a lot more peers than seeders, this is really impressive

So far it looks like this will be my default client from now on.

What do think about qBittorrent? Please specify pros and cons.

Do you know that a new version of KTorrent was released today? It separates the Bit Torrent functionality into its own library, which should reduce bloat because things like KGet will be able to share code with it in the future.

Anyway, have you tried KTorrent 4.0.0?

---

### Post by lovinglinux on 2010-05-29
> **Shining Arcanine said:**
> Anyway, have you tried KTorrent 4.0.0?

No. I didn't want to compile it. Does it look good?

---

### Post by Shining Arcanine on 2010-05-29
> **lovinglinux said:**
> No. I didn't want to compile it. Does it look good?

It looks fine to me, although since it just came out today, I have not had a chance to do many torrent downloads with it.

---

### Post by Charles Kerr on 2010-05-29
> **lovinglinux said:**
> What do think about qBittorrent? Please specify pros and cons.

As you'd probably expect, my obligatory recommendation is [Transmission]("http://www.transmissionbt.com").  But we've been through that before so I'll set that aside... :)

**Pro**: qBitTorrent has a clean, easy interface, and uses a good backend (libtorrent-rb, the same as Deluge).  KDE users who want a uTorrent-like interface but find KTorrent too heavy could do much worse than qBitTorrent.

**Pro**: according to [this client "shootout"]("http://pastehtml.com/view/5tx16jw.html"), qBitTorrent uses about 10 MiB less memory than KTorrent.

**Con**: it's banned on *many* private trackers because of its feature for spoofing other clients' peer-ids.  I guess that could be a "pro" too since you can use that spoofing feature to get around the ban anyway... but it seems distinctly antisocial for a BitTorrent client IMO.

---

