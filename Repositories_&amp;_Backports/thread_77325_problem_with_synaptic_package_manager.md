---
title: "problem with synaptic package manager"
date: 2005-10-16
forum: Repositories &amp; Backports
---

### Post by sumedha on 2005-10-16
i can instal any package as when i open synaptc package manager i get a warning 
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)

i tried using xterm but i get the same message

---

### Post by UbuntuUbuntu7 on 2005-10-17
I get the same message directly when i enter Synaptic, but it seems that i can install things anyway. I get get the message allso when i uninstall something: 

[I]"Warning

The following problems was found on your system:

W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/se.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/se.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/se.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/se.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 Filen eller katalogen finns inte)"[/I]


Anybody know what this is? I allso get it when i go through the "add applications" tab.

---

### Post by lundse on 2005-11-19
I get the same thing, it started after I installed something.

---

### Post by jdong on 2005-11-21
Try reloading several times....


This is not a Backports related problem.

---

### Post by aysiu on 2005-11-21
See the first link in my sig, particularly the bottom part.

---

### Post by frogfromsaturn on 2005-11-22
I followed the instruction on updating the repositories and when I try 
sudo apt-get update
I get a timed out message. I also used to get the stat message I could never do anything when that happens. Now I still get the stat message but it starts downloading package information but the progress bar doesn't budge. It shows that it failed on every file. 

I'm connected to the internet directly via an ADSL/Router and that is the means I'm using in Ubuntu to write this message but it doesn't seem to be working for updates. Please help. :(

---

### Post by aysiu on 2005-11-22
It could be a firewall thing... unfortunately, I know very little about how to fix that, but that's all I can think of.

---

### Post by sjhawtin on 2005-11-23
This post may hold the solution for you. I had a similiar problem and it solved it. 
(Post No. 2) [http://www.ubuntuforums.org/showthread.php?t=11544](http://www.ubuntuforums.org/showthread.php?t=11544)

Note: If you are using Breezy, you should not follow the last step and comment out what it says but instead comment out the line # mv $new_resolv_conf /etc/resolv.conf

I was directed to it from this post (it is the 2nd of 2 links in option 3).
(Post No. 4) [http://www.ubuntuforums.org/showthread.php?p=425483](http://www.ubuntuforums.org/showthread.php?p=425483)

---

