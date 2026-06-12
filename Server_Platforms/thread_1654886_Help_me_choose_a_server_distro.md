---
title: "Help me choose a server distro"
date: 2010-12-29
forum: Server Platforms
---

### Post by lkejke on 2010-12-29
What distribution would you recommend if I have the following needs:

- Router for my local network (via USB wireless dongle)
- Provide VPN* to my home country (I live overseas).
- Run a web server with PHP and MySQL for web development.
- SSH server and client.
- Provide security for my local network (firewall etc.).
- Attach network storage via USB (for backup and large media files).
- Run everything from the terminal (no GUI).
- Full control over packages and configuration.
- Can easily update packages for security updates.

I'm an beginner-intermediate Linux user.
I am running Ubuntu 10.10 on my desktop.
I don't think Linux From Scratch (LFS) is within my ability yet.

Also, I'm trying to choose a suitable device to run this server. I'm thinking about an SSD netbook. But a fanless device would be even nicer. That would probably mean an unusual chip architecture, which means compiling from source, right? Maybe even running an embedded system (which I don't fully understand).

Any tips would be great.

Also, maybe LFS isn't toooo difficult. What do you think?

---

### Post by WinstonChurchill on 2010-12-29
Ubuntu would be able to do everything you've mentioned, and it is extremely easy to maintain. Aptitude (the package manager) is almost foolproof. Ubuntu also uses very recent kernels (2.6.35 right now - and the latest stable from kernel.org is 2.6.36) - for me that's a big plus.

I am a huge fan of using laptops/netbooks as servers - not only do they use much less power, but they have built-in battery backups. I would go after one with at least 2GB of RAM and multiple cores if you can, but you could very likely get by with somewhat less than that, depending on exactly how much use it will get. If you want it to act as a wifi AP, make sure the internal card (or whatever USB dongle you choose to buy) is compatible with hostapd (google it and you can find their list - there are cards that work that aren't on that list, however). I wouldn't use an SSD however - it's a bit of a waste to have one in a server, especially if you're using external storage. 

I wouldn't worry about finding a fan-less setup - there's really very little reason to, as laptop/netbook fans draw next to no power, and make next to no noise.

---

### Post by lkejke on 2010-12-29
> **WinstonChurchill said:**
> Ubuntu would be able to do everything you've mentioned, and it is extremely easy to maintain. Aptitude (the package manager) is almost foolproof. Ubuntu also uses very recent kernels (2.6.35 right now - and the latest stable from kernel.org is 2.6.36) - for me that's a big plus.

I am a huge fan of using laptops/netbooks as servers - not only do they use much less power, but they have built-in battery backups. I would go after one with at least 2GB of RAM and multiple cores if you can, but you could very likely get by with somewhat less than that, depending on exactly how much use it will get. If you want it to act as a wifi AP, make sure the internal card (or whatever USB dongle you choose to buy) is compatible with hostapd (google it and you can find their list - there are cards that work that aren't on that list, however). I wouldn't use an SSD however - it's a bit of a waste to have one in a server, especially if you're using external storage. 

I wouldn't worry about finding a fan-less setup - there's really very little reason to, as laptop/netbook fans draw next to no power, and make next to no noise.

Excellent. Thanks for the advice.

---

### Post by snowpine on 2010-12-29
Some great info on running an Ubuntu server:

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

I would recommend sticking with the LTS releases (currently 10.04) as there is no need to release-upgrade a server every 6 months.

Other popular server distros include Debian Stable, CentOS, Slackware, etc. but why not use your existing Ubuntu knowledge? :)

---

### Post by HermanAB on 2010-12-29
Linux is Linux is Linux...

Which car is better, the black one or the red one?

However, if you want wizards to help configuring your system, then you should look at the older distros like Mandriva or Suse.

---

