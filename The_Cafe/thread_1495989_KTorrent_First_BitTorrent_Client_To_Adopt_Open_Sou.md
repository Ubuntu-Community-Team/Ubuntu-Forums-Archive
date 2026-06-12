---
title: "KTorrent First BitTorrent Client To Adopt Open Source uTP"
date: 2010-05-28
forum: The Cafe
---

### Post by lovinglinux on 2010-05-28
Read the full article at [TorrentFreak](http://torrentfreak.com/ktorrent-first-bittorrent-client-to-adopt-open-source-utp-100528/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+Torrentfreak+%28Torrentfreak%29).

> The KDE BitTorrent client KTorrent has become the first to implement the ‘improved’ BitTorrent protocol that was open sourced by BitTorrent Inc. a few days ago. With uTP, KTorrent users should cause less network congestion and interference with other applications. They are also the first to benefit from faster connections to uTorrent users.

> To our knowledge, KTorrent is the first client outside BitTorrent Inc. to implement uTP support. With uTP, KTorrent will be more network aware as it will throttle itself if congestion is detected in the network. In theory, this should eliminate the need for ISPs to throttle BitTorrent traffic, while KTorrent users should see less interference with other local applications.

What do you think?

---

### Post by Shining Arcanine on 2010-05-28
I think that the title should be "KTorrent First Open Source BitTorrent Client To Adopt uTP", because I believe that uTorrent was the first BitTorrent client to adopt uTP.

Anyway, I run Gentoo Linux and received the upgrade earlier today. A great deal of the code has changed. I have not had much time to play with it, but I did notice that now it exists as two separate packages, libktorrent ktorrent. I wonder if kget's Bit Torrent functionality will be modified to utilize libktorrent. That is all I can say about it for now.

---

### Post by lovinglinux on 2010-05-28
> **Shining Arcanine said:**
> I think that the title should be "KTorrent First Open Source BitTorrent Client To Adopt uTP", because I believe that uTorrent was the first BitTorrent client to adopt uTP.

Yes, I agree, but that is the title of the original article.

> **Shining Arcanine said:**
> Anyway, I run Gentoo Linux and received the upgrade earlier today. A great deal of the code has changed. I have not had much time to play with it, but I did notice that now it exists as two separate packages, libktorrent ktorrent. I wonder if kget's Bit Torrent functionality will be modified to utilize libktorrent. That is all I can say about it for now.

I wonder if anyone is willing to create a PPA? I don't want to install all the dependencies to compile it.

---

### Post by Shining Arcanine on 2010-05-28
Here is the dependency graph from Gentoo's package manager:

>  * dependency graph for net-p2p/ktorrent-4.0.0
 `--  net-p2p/ktorrent-4.0.0  ~x86 
  `--  net-libs/libktorrent-1.0.0  (>=net-libs/libktorrent-1.0_rc1) ~x86 
  `--  media-libs/taglib-1.6.3  (>=media-libs/taglib-1.5) ~x86 
  `--  kde-base/libtaskmanager-4.4.3  (>=kde-base/libtaskmanager-4.4) ~x86 
  `--  kde-base/kdepimlibs-4.4.3  (>=kde-base/kdepimlibs-4.4) ~x86 
  `--  kde-base/solid-4.4.3  (>=kde-base/solid-4.4) ~x86 
  `--  kde-base/libkworkspace-4.4.3  (>=kde-base/libkworkspace-4.4) ~x86 
  `--  kde-base/kdelibs-4.4.3  (>=kde-base/kdelibs-4.4) ~x86 
  `--  dev-libs/geoip-1.4.6  (>=dev-libs/geoip-1.4.4) x86 
  `--  app-arch/unzip-6.0-r1  (app-arch/unzip) x86 
  `--  kde-base/kdebase-kioslaves-4.4.3  (>=kde-base/kdebase-kioslaves-4.4) ~x86 
  `--  kde-base/krosspython-4.4.3  (>=kde-base/krosspython-4.4) ~x86
[ net-p2p/ktorrent-4.0.0 stats: packages (12), max depth (0) ]

---

### Post by lovinglinux on 2010-05-28
> **Shining Arcanine said:**
> Here is the dependency graph from Gentoo's package manager:

I was referring to build-essential dependencies. Anyway, I'm setting up a VM to do that. I'm not sure it will work, but I will try.

---

