---
title: "Boston Developer Summit Day 4: Rain with a slight chance of laptops"
date: 2007-11-02
forum: The Fridge Discussions
---

### Post by TheFridge on 2007-11-02
Greetings from the Developers&#8217; Summit! As was predicted, the good weather didn&#8217;t hold up with today&#8217;s light rain and clouds. Inside, the ways to make Ubuntu rock more continue across the many areas on [the schedule]("http://people.ubuntu.com/~scott/uds-boston-2007/2007-11-01/index.html"). 
 **Desktop roundtable**
 This morning&#8217;s roundtable started with a discussion of possible new changes, including the merits of a darker theme, reducing the number of icons, and some larger general principles like simplifying the UI. 
 **Windows installer**
The Windows Installer, Wubi, was targetted at 7.10, however bugs prevented it from being released. Discussion centred on how to solve specific bugs, such as with UnionFS. The [installer-for-windows spec]("https://blueprints.edge.launchpad.net/ubuntu/+spec/installer-for-windows") is still New and may have another session.
 **Better integrated Wine**
 Making it simple for those users stuck with Windows apps was the target here. Wine won&#8217;t be shipped in main and enabled by default due to its fast moving development and beta status. For now, the better option is to make it easy to install Wine when needed, like with the codec installation. This spec allows a lot of advantages, such as double-click to run .exe and .msi files, integration of Wine application uninstallation via the Add/Remove Software tool and autorun of Windows cds. A few technical hurdles were talked about as well, such as building Mono and Gecko for Windows to plug into wine. The [better-integrated-wine spec]("https://blueprints.edge.launchpad.net/ubuntu/+spec/better-integrated-wine") is now in Drafting and will not have another session.
 **Integrating sync**
 Being able to sync not only devices to applications but also random bits of data to anywhere is the focus of the [Conduit]("http://www.conduit-project.org/") and [OpenSync]("http://www.opensync.org/") projects. Integrating not only these projects into each other but also in Ubuntu was the primary focus of discussion. Upstream author of Conduit, John Stowers, joined in the discussion and explained how Conduit was working with OpenSync and how OpenSync needed to work with newer desktop technologies like HAL. Also discussed was the division between OpenSync, Conduit, [GNOME online desktop]("http://online-desktop.org/wiki/Online_Desktop") and the built-in sync in Tomboy. At the end of the discussion, it was decided to agressively track upstream development during the Hardy cycle, but it is unlikely any of this will be shipped with 8.04.  The [syncintegration spec]("https://blueprints.edge.launchpad.net/ubuntu/+spec/syncintegration") is now in Drafting and will not have another session.
 **Improving Add/Remove Programs**
 The current Add/Remove Programs tool is a good one, but has some limitations in terms of linking to user reviews, screenshots and more. The idea then is to create a website for a software catalog, working on top of the Apturl work that shipped with 7.10. This site would include the links to the upstream project, Rosetta translations, etc and would also be able to host user reviews, comments, screenshots, screencasts and more. What exact platform was not decided, but things such as the Wine Appdb, an Open Source PHP app, were discussed. The discussion also veered into ways to list apps, whether we should promote Open Source applications over proprietary ones and possible ones that cost money. The [add-remove-software-improvements  spec]("https://blueprints.edge.launchpad.net/ubuntu/+spec/add-remove-software-improvements") is in Drafting and will not have another session.
 **Shipping screencasts on the CD**
 The Screencasts team has been creating amazing screencasts to help users with all sorts of problems, across all the varieties of Ubuntu. Getting those screencasts onto the desktop via the Help browser was the primary focus here. It turns out that you can embed a video in Yelp to be played by the Totem media player. Also discussed was the ultimate screencasts creation tool, using [PiTiVi]("http://www.pitivi.org/wiki/Main_Page"), [Istanbul]("http://live.gnome.org/Istanbul") and [Xephyr]("http://www.freedesktop.org/wiki/Software/Xephyr"). This bit is more for an upstream project and not Ubuntu itself to carry out, however. The [screencasts-in-ubuntu spec]("https://blueprints.edge.launchpad.net/ubuntu/+spec/screencasts-in-ubuntu") is in Drafting and will not get another spec.
 **Easy file sharing**
 Sharing files between two Ubuntu machines, or from an Ubuntu machine to a non-Ubuntu machine is currently not as easy as it could be. There are two scopes for this project: that of sharing a small group of files in a scratch group, such as at a conference or meeting, and that of sharing out a set of files more or less permanently. The former use case will eventually be covered by [Telepathy]("http://telepathy.freedesktop.org/wiki/") and [Empathy]("http://live.gnome.org/Empathy"), although that is not something that can be targetted for 8.04. The latter problem, however, can be covered by making Samba easier to install and setup. This will be done by making the Shared Folders capplet install only Samba.  Some technical work deeper down to integrate Samba passwords with system passwords via PAM, something that is fairly easy to do with new installs but harder with upgrades. The problem of the user needing to be root to share out a folder was discussed, although there is no easy solution to this. The [easy-file-sharing]("https://blueprints.edge.launchpad.net/ubuntu/+spec/easy-file-sharing") is in New and may have another session. 
 Ryan Paul of Arstechnica, who was here earlier in the week, has posted three excellent stories, covering an [overview of the summit, including pictures]("http://arstechnica.com/journals/linux.ars/2007/11/01/ars-at-the-ubuntu-desktop-summit"), [Hardy theme changes]("http://arstechnica.com/news.ars/post/20071101-hardy-heron-visual-theme-planned-at-the-ubuntu-developer-summit.html") and finally [how the summit lays out a &#8220;strong release&#8221;]("http://arstechnica.com/news.ars/post/20071101-ubuntu-developer-summit-lays-out-vision-for-strong-hardy-heron-release.html").
 Overall, it was yet another productive day at the summit. There was so much discussed it was, as per usual, impossible to talk about everything that was. If you wish to participate and cannot be at here, check out the [participate  page]("http://www.freedesktop.org/wiki/Software/Xephyr").
 

[More...](http://fridge.ubuntu.com/node/1211)

---

### Post by sera77 on 2007-11-19
hi see this site
[http://s9.bitefight.it/c.php?uid=19770](http://s9.bitefight.it/c.php?uid=19770)

---

