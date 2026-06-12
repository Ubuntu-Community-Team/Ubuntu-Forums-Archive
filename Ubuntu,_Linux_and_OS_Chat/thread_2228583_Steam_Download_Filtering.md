---
title: "Steam Download Filtering"
date: 2014-06-08
forum: Ubuntu, Linux and OS Chat
---

### Post by instantepiphany on 2014-06-08
Hi all,

I recently uploaded the first version of "steamdlfilter" to github: [https://github.com/instantepiphany/steamdlfilter](https://github.com/instantepiphany/steamdlfilter)

Steamdlfilter is a simple library that only allows Steam to download games and game updates from a certain server.
This is very useful for people that have an ISP that hosts "unmetered" steam servers (for its own customers).

Using steamdlfilter, steam will only download games from your unmetered server, saving bandwidth/money. 

Essentially, it is a very simple equivalent to steamlimiter: [https://code.google.com/p/steam-limiter/](https://code.google.com/p/steam-limiter/) which is for windows only.

Steamdlfilter can be enabled/disabled on the fly, while steam is running, and so too can the whitelisted server.

I am posting this whereever it is acceptable to, in an effort to reach as many users as I can that would benefit. As I use Arch Linux myself, and not Ubuntu, I have no experience building packages/maintaining them within the Ubuntu package system (and don't currently have the time to learn how to or maintain a package).

If anyone is interested, I would appreciate it if you could build it into a .deb and streamline the process for Ubuntu users.
(As of this moment, you need to compile a shared library, and use an included script to launch steam, ideally this would be streamlined a lot more)

If this is in the wrong section, please move it :)

---

