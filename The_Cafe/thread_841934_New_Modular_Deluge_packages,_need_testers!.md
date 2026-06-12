---
title: "New: Modular Deluge packages, need testers!"
date: 2008-06-26
forum: The Cafe
---

### Post by zachtib on 2008-06-26
If you're already running Deluge 0.6 from my PPA, you should get this as an update.

As you may know, the big feature in Deluge 0.6 is the ability to separate the frontend and backend of the client.  Until now, however, it was still packaged as one binary, which meant you had to install the whole thing regardless of if you only wanted a single part or not, which could bring in unneeded dependencies.  However, I've now split the package into multiple binaries:

deluge-torrent-0.6: meta-package to pull down everything
deluge-0.6-gtk: GTK user interface
deluge-0.6-webui: Web user interface
deluge-0.6-client: Console user interface and common files for GTK/Web UIs
deluge-0.6-plugins: Deluge Plugins
deluge-0.6-server: The daemonized backend
deluge-0.6-common: Common files for all packages.

Note that this is still fairly experimental, but if can can, please test and report any problems you have, either in this thread, or you can PM/email me.


To install, visit:

[https://launchpad.net/~zachtib/+archive](https://launchpad.net/~zachtib/+archive)

---

