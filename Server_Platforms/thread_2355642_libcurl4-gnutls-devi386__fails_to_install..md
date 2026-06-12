---
title: "libcurl4-gnutls-dev:i386  fails to install."
date: 2017-03-14
forum: Server Platforms
---

### Post by acdcman200 on 2017-03-14
Hello,

I need to install libcurl4-gnutls-dev:i386 on a 16.04.2 (64bit) server for a game server. I tested this string in vm's with success but on the production system it fails.

dpkg --add-architecture i386; sudo apt-get update;sudo apt-get install mailutils postfix curl wget file bzip2 gzip unzip bsdmainutils python util-linux tmux lib32gcc1 libstdc++6 libstdc++6:i386 libcurl4-gnutls-dev:i386

Output for apt install libcurl4-gnutls-dev:i386

[http://pastebin.com/raw/F4Yf605i](http://pastebin.com/raw/F4Yf605i)

Things tried

Fully updating the system, reboot.
dpkg --configure -a
apt -f install
rm /var/cache/apt/archives/libcurl4-gnutls-dev_7.47.0-1ubuntu2.2_i386.deb 
apt install ibcurl4-gnutls-dev:i386 still results in the same issue

Any ideas what could case this to pass in testing then fail on this specific system? What logs do you want to look into?

Thanks

---

