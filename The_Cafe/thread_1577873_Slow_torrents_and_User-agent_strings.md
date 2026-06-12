---
title: "Slow torrents and User-agent strings"
date: 2010-09-19
forum: The Cafe
---

### Post by renkinjutsu on 2010-09-19
I've had some trouble downloading old torrents in the past. When the amount of seeders is about the same as the amount of peers in the "swarm" deluge seems to have trouble downloading at speeds above 15 KiB/s for me, but my upload is maxing out at the top speed my settings allow (42-47 KiB/s)(also, the average peer was at 70% while I was at 0.5%) .. Normally, deluge maxes out both upload and download in a "healthy" torrent.

I've always thought "Oh.. the torrent just doesn't have a healthy seed to peer ratio"

I was curious, so i clicked the "peers" tab on deluge, and I saw that out of the 10 clients that i was connected to two were using Azureus and the rest were using µTorrent. So I tried downloading the torrent again with µTorrent (using the downloaded pieces from deluge as a base), and µTorrent starts maxing out my speeds! And what else? µTorrent was not uploading any data AT ALL!

µTorrent is FAST, but it seems to ignore the philosophy of bittorrent, since the idea is that everyone utilizes their own bandwidth to share and distribute bits of a file(s). I think what they're doing is pretty detrimental to the health of torrents. Theoretically, a torrent should still be "healthy" as long as there are a couple of seeds in the swarm because everyone will help distribute right? I miss bittornado.

What do you guys think? have you noticed this with µTorrent?

---

### Post by lovinglinux on 2010-09-19
Although all clients work basically the same, there are some differences between clients implementations of various technologies (DHT,PEX,Encryption), notably with Azureus and uTorrent. For instance uTorrent has the uTP protocol that could be influencing your final speed. I'm not sure if Deluge already has such protocol implementation.

Nevertheless, I think some clients might in fact prioritize peers with similar clients. I think this is why qBitTorrent is the fastest client I ever used, because it can spoof the client ID to look like uTorrent.

---

