---
title: "Using IPTables with KTorrent"
date: 2013-02-05
forum: Security
---

### Post by Stonecold1995 on 2013-02-05
I'd like to set up iptables and set the default policy to drop connections that I don't manually whitelist.  The problem is that I also run KTorrent, which connects to peers with random ports.  Is there a way I can configure iptables to ignore any connections handled by KTorrent but block everything else?

---

### Post by Soul-Sing on 2013-02-05
I don't know but isn't an idea to use moblock/peerblock together with torrent connections? How it integrates with iptables is the question I can't answer.
As said ports are random given via torrent connections.
Transmission uses 51413/tcp, 51413/udp, 6969/tcp

---

### Post by Stonecold1995 on 2013-02-05
I use KTorrent's built-in peer blocking (which gets the "bad" IP list from the same source as PeerBlock).  I don't want to set up iptables to protect KTorrent, I want to set up iptables and have it *ignore* KTorrent.  Because iptables has no way of knowing if an incoming IP/port is malicious or simply a peer, it would either have to block them all (which I don't want), or be off (which I also don't want).  I'm looking for a way for iptables to be "application aware" and allow any incoming/outgoing connections if they are going through KTorrent, but have its rules still apply to other connections.

---

