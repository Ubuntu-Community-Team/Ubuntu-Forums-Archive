---
title: "My Deployment is nearing completion. Proud and love Ubuntu!"
date: 2018-05-14
forum: Ubuntu, Linux and OS Chat
---

### Post by Tadaen_Sylvermane on 2018-05-14
I've been slowly working up to my full HTPC deployment over the last year or so. Money has been tight so it's been a slow process.

What I've done, and am proud of.

Living room htpc is Ubuntu Xenial LTS direct booting to Kodi. This htpc functions as my main server in the home. It manages dhcp, dns, backup dns, apt-caching proxy, transmission server, mythtv-backend, backup target for all laptops in the house, and ltsp server. Also 4 minecraft servers, all running in ramdisks.

My storage is currently barely 39% of 2.4tb total available space. The pool is managed via mergerfs backported from bionic. Data protection provided by snapraid. That 39% contains over 500 movies, 1000+ episodes of tv shows, and 5-6 gigs of music.

Most of it is self-explanatory however the ltsp is unique in my setup. I've yet to find someone else doing what I'm doing with it. I have 3 satellite media centers around the house, none with local storage. They all pxe boot via ltsp from the main htpc in the living room straight to Kodi. I am maintaining 3 separate video databases for kodi, and a single music db. one db servers master bedroom, living room, and the wife and I's tablets / phones / computers. The other 2 databases are 1 for each guest room. All music is a single db to every room. 

I am maintaining a desktop use ltsp chroot, however I currently only use that to rip dvds on the wife's computer (she runs windows). My dvd drive went out on my laptop. Ultimate goal is to have at least 2-3 desktops running off of ltsp around the house, including my own workstation.

I am experimenting with homeassistant inside an lxd bionic container right now. 


I love Ubuntu. The only thing I can't get working right is a print server, however a Debian container with LXD solves that issue 100%. All other containers, ltsp chroots and host is Ubuntu Xenial LTS. None of this would be possible without it. This type of thing has been a long goal of mine from the time I started learning linux. Thank you Canonical... even though you will likely never see this post. That and the people on this forum have provided a fair bit of help as well. I appreciate it all from everyone.

---

