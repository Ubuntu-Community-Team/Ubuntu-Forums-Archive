---
title: "synaptic package manager says I have problems"
date: 2005-10-26
forum: Repositories &amp; Backports
---

### Post by tmtjjhnsn on 2005-10-26
Can anyone tell me why I get this message when I start Synaptic?  I am an eager but ambitious newbie who could use some help.

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by towsonu2003 on 2005-10-26
I'm a newbie, so you may wanna wait for someone else to reply..

Basically, you have to remove "us" (the mirror) in your repository [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com). so it will be [http://archive.ubuntu.com](http://archive.ubuntu.com)

While waiting for another reply, try to search for a clean repository list (sources.list) in the forums...

---

### Post by ecobuntu on 2005-10-27
[QUOTE=tmtjjhnsn]Can anyone tell me why I get this message when I start Synaptic?  I am an eager but ambitious newbie who could use some help.

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)[/QUOTE]

Just try it again in about 30 minutes when this happens.

sudo apt-get update
sudo apt-get upgrade

---

