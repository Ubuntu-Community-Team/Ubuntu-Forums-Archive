---
title: "Installing software on 17.04"
date: 2017-03-15
forum: Ubuntu Development Version
---

### Post by simonsaysthis on 2017-03-15
Hi all

In general 17.04 is very usable to me. There is however one rather big issue, I can't seem to install downloaded deb files.

Tried Skype Beta and Adobe flash and in both instances it doesn't work. Tried via software centre and manually. Is this a bug or related to the dev version. Is there a workaround for this?

thanks so much

---

### Post by howefield on 2017-03-15
Seems to install well enough, can you expand on exactly how you tried to install and what fails ?

```
sudo apt install ~/Downloads/skypeforlinux-64.deb
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'skypeforlinux' instead of '/home/hugh/Downloads/skypeforlinux-64.deb'
The following NEW packages will be installed
  skypeforlinux
0 to upgrade, 1 to newly install, 0 to remove and 0 not to upgrade.
Need to get 0 B/50.7 MB of archives.
After this operation, 165 MB of additional disk space will be used.
Get:1 /Data/Downloads/skypeforlinux-64.deb skypeforlinux amd64 5.0.0.5 [50.7 MB]
Selecting previously unselected package skypeforlinux.
(Reading database ... 180799 files and directories currently installed.)
Preparing to unpack .../Downloads/skypeforlinux-64.deb ...
Unpacking skypeforlinux (5.0.0.5) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu2) ...
Setting up skypeforlinux (5.0.0.5) ...
Processing triggers for bamfdaemon (0.5.3+16.10.20160929-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu5) ...
Processing triggers for hicolor-icon-theme (0.15-1) ...
```

[ATTACH=CONFIG]274158[/ATTACH]

---

### Post by simonsaysthis on 2017-03-15
Thanks for the quick response. So gdebi solves the issue. I think its a software centre glitch

---

### Post by howefield on 2017-03-15
> **simonsaysthis said:**
> Thanks for the quick response. So gdebi solves the issue. I think its a software centre glitch

Can't test with the Software Centre as it's the first thing I uninstall, even on the development version. There is one small glitch and that is the lack of a Skype panel icon.

---

### Post by jbicha on 2017-03-15
Yes, the Software app currently can't install 3rd party .debs. This regression also affects 16.04 LTS and 16.10. ([LP: #1672424]("https://launchpad.net/bugs/1672424"))

---

