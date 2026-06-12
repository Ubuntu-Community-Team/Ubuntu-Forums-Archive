---
title: "Install basic desktop on top of server?"
date: 2007-05-31
forum: Server Platforms
---

### Post by PopcornEaterMan on 2007-05-31
Hi, I would like to install a ubuntu as a server because I plan to use it that way for about 90% of the time, and I like the features.. LAMP, etc.  I would occasionally like to use the GUI desktop for websurfing and torrent downloading and some administration.  Is it possible to get the KDE/Gnome desktops without all of that open office, and other utilities that come with normal desktop ubuntu?

---

### Post by craigp84 on 2007-05-31
Hi PopcornEaterMan,

Unless hard disk space is a constraint, it really doesn't matter. Just install the full desktop edition.

There can be serious consequences if you only install part of the ubuntu-desktop come upgrade time. You can arrive at a situation where a new component is required for your desktop to work, however, apt cannot figure out to install that component due to the way packaging has to work.

Don't worry about the difference between ubuntu desktop edition, and ubuntu server edition. At this point, the server edition really should be thought of as "ubuntu basic edition" it's a slimmed down version of the desktop edition, there;s nothing that makes it more server oriented other than a different kernel which can be apt-get installed if you need it (you don't :) ).

All that being said, you can install the server editon, and apt-get selective components and it will work absolutely fine. It will only take longer to maintain and more messing around.

Hope this helps,

Craig

---

### Post by PopcornEaterMan on 2007-05-31
Excellent points there.  Does that mean that the full-desktop version has LAMP preinstalled?  I thought that in the past, LAMP came preconfigured with server, but not with the desktop.

---

### Post by craigp84 on 2007-05-31
It comes preconfigured in neither unfortunately.

It can be chosen as an option during the server install, and it can be chosen as an option in desktop or server after installation.

6 and half a dozen really.

-c

---

### Post by PopcornEaterMan on 2007-05-31
Thanks, I suppose I am distracted when I look through the menus.. "Games? I don't need those. Anjuta? don't need it.." so on and so on.  I'm just looking for a slightly leaner system in some ways.  Is it safe to uninstall games and the IDE using synaptic?

---

### Post by craigp84 on 2007-05-31
Yep. Anjuta's not part of the base install. The games are though.

You can still uninstall them, you're not going to kill anything - just be careful around upgrade time.

alternatively right click on applications menu button and choose edit menus. Hide the one's you don't want to be clicking on :-)

-c

---

