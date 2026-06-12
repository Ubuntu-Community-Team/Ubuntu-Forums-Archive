---
title: "btlaunchmany missing options / old version?"
date: 2006-07-14
forum: Server Platforms
---

### Post by stonecipher on 2006-07-14
I have 6.06 Server installed and all patched up and am wanting to run BitTorrent via btlaunchmany but I seem to be missing some command line options.

Specifically I can not get the --save_in or --torrent_dir options to be recognized from the command line.  I believe this is related to the version of BT that is available in the repositories.  While the current version from [www.bittorrent.com](www.bittorrent.com) is 4.20.4, the version installed with Server (and in the repositories) is 3.4.2 which is from 2004-04-04.  

While I could install the .deb from bittorrent.com I would prefer to apt-get from the official repositories since there are many dependencies. 

Any help on getting the command line options working or getting an updated version appreciated.

Thanks.

---

### Post by stonecipher on 2006-07-29
Problem solved.

$sudo apt-get install rtorrent

I still think that a more recent version of bittorrent ought to be packaged with the distro.  Could someone please point me to where I can find the maintainer of the bittorrent package?

Thanks.

---

