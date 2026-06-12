---
title: "Howto automatically check and download updates using TOR"
date: 2017-04-01
forum: Security
---

### Post by Floppyjoe on 2017-04-01
To get your Ubuntu system to automatically use the TOR network when checking for updates and downloading updates via apt, you can use the file apt-transport-tor.

sudo apt-get install apt-transport-tor

You need to update your sources.list file, and other .list files in the apt directories. They are found at /etc/apt/sources.list and if you have non-Ubuntu sources they are in the directory /etc/apt/sources.list.d/filename_goes_here.list

in the .list files you need to add "tor+" before the "http://" part of all the repositories that are not commented out.

It will look something like "deb tor+http://repository_information_goes_here".

These changes assume you have TOR installed.

---

