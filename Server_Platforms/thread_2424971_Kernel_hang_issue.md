---
title: "Kernel hang issue"
date: 2019-08-18
forum: Server Platforms
---

### Post by alistairw2 on 2019-08-18
Hi,

I've experienced three kernel hangs over the past two weeks. I've contacted my host (Hetzner) who have told me that it is likely to be a software fault and if I want them to diagnose the software it will require all of the elements stripped from the server and tested which may take up to 14 hours. I would like to ensure that is most likely a hardware fault (such as a NIC card) and that it is absolutely necessary before requesting a full hardware diagnostic from Hetzner.

I&#8217;m currently running Ubuntu 18.04.3 LTS with 4.15.0-58-generic kernel. 

I managed to find some information about the error on the internet and tried ```
ethtool -K enp0s31f6 gso off gro off tso off
``` although the latest hang still happened yesterday. 

There are two Syslogs which I have uploaded below, they're from separate days:
[https://pastebin.com/VsHUFtjB](https://pastebin.com/VsHUFtjB)
[https://pastebin.com/rEdnAkiD](https://pastebin.com/rEdnAkiD)

The server only hosts a [https://pterodactyl.io/](https://pterodactyl.io/) daemon hosts docker containers with Minecraft servers inside of them.

Any help would really be appreciated :grin:

---

