---
title: "apt-get install problem in ubuntu 9.04 server"
date: 2009-10-16
forum: Server Platforms
---

### Post by emiller1404 on 2009-10-16
I've recently installed jaunty server edition on an old computer at home and was moving along fine for a while but I've hit a snag that seems to have me stumped. 

I set up EBOX to administer a samba server I've got running on it and I can connect to the shared folders from my other computer on the network. I then logged on to the server and tried to install rtorrent at a CLI - 

[FONT="Courier New"]wyn-0:~$ sudo apt-get install rtorrent

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libcurl3 libtorrent11 libxmlrpc-c3
The following NEW packages will be installed:
  libcurl3 libtorrent11 libxmlrpc-c3 rtorrent
0 upgraded, 4 newly installed, 0 to remove and 119 not upgraded.
Need to get 1123kB of archives.
After this operation, 2871kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  libcurl3 libxmlrpc-c3 libtorrent11 rtorrent
Install these packages without verification [y/N]? y
0% [Connecting to security.ubuntu.com (91.189.88.37)][/FONT]

and it just hangs here. I didn't have this problem before I set up EBOX- is it causing the problem? Or is there something else going on?

---

