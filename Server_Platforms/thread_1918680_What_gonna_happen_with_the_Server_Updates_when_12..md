---
title: "What gonna happen with the Server Updates when 12.04 Desktop come out?"
date: 2012-02-01
forum: Server Platforms
---

### Post by Wisdown on 2012-02-01
Hi all,

The first thing i need say is english isnt my native language, but, i hope you guys can understand my questions :D
I'm on my 3rd week runing an Ubuntu Server as desktop.
I instaled the LTS version Lucid 10.04, then i have installed the desktop using:

```
sudo apt-get install ubuntu-desktop
```My first question is what gonna happen when the Desktop Version 12.04 come out?
When i do the updates i will lose my entire Desktop for the new version? My settings will be erased (example compiz)?

My goal using the server edition, is have an "Desktop PC" able to host my personal websites, for my personal websites i will make 3 virtual machines (WEB + Email + Database). I read the server version is optmized for network this is why i choosed start by the server edition.
I did the right choice or i would install the Desktop version as Host and Server Version as Guests (Virtual Machines)?

Ty so much for the help

---

### Post by sanderd17 on 2012-02-01
Normally, when you upgrade, all settings will be kept, and all programs will still be there (just a newer version). Only the settings that aren't compatible with 12.04 will be changed. Compiz settings can be changed as a result of that (and probably will, as Unity uses Compiz).

The server edition is probably what you want. So no problem with that, although the desktop edition can do the same.

For you, I would wait with upgrading to 12.04 until all bugs are removed. wait at least 3 months, and read the release notes.

---

### Post by Wisdown on 2012-02-01
> **sanderd17 said:**
> Normally, when you upgrade, all settings will be kept, and all programs will still be there (just a newer version). Only the settings that aren't compatible with 12.04 will be changed. Compiz settings can be changed as a result of that (and probably will, as Unity uses Compiz).

The server edition is probably what you want. So no problem with that, although the desktop edition can do the same.

For you, I would wait with upgrading to 12.04 until all bugs are removed. wait at least 3 months, and read the release notes.

Thanks for the answer.
So let me see if i get what gonna happen.
As soon Desktop 12.04 come out as final LTS release my next update will change the gnome desktop to lucid is it (since the LTS repository will change)? But my kernel and server will be 10.04 (there support till April 2015 for server LTS)?

---

### Post by sanderd17 on 2012-02-01
No, when 12.04 comes out, you will get the ability to upgrade (wheter you get a notification or not depends on your settings). If you just continue doing the things you do, you can use 10.04 for 3 more years (although, since you use the ubuntu-desktop package, I advise to upgrade during the coming year).

---

### Post by TheFu on 2012-02-01
Ubuntu does not force an upgrade between OS versions.  So your 10.04 settings for desktop and server will not be forced to 12.04.  You will have to manually do something for that to happen. It will be clear, nothing hidden.

I think the only issue will be that 10.04 desktop updates will stop as desktop distros go out of support much quicker than server distros. That could become a security concern.

BTW, I also run "server LTS" as my base, but I use LXDE for my desktop.  I'll wait to update at least a month after 12.04 LTS is released.

---

### Post by Wisdown on 2012-02-01
Got it!!!
I gonna stay with my 10.04 Server and use your hint guys, 3 months after the release i  do the upgrade.
Thanks all for the support.

---

