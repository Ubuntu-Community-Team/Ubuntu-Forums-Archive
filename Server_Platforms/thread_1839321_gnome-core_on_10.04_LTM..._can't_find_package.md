---
title: "gnome-core on 10.04 LTM... can't find package??"
date: 2011-09-05
forum: Server Platforms
---

### Post by gorbenzer on 2011-09-05
Hello everyone!
I just setted up a new server with ubuntu 10.04 LTM server edition and i would like to install gnome-core but i can't retrieve the package it says there are no packeges with that name...

can you help me? have the package name changed or i need to add a repository??

Thanks!

---

### Post by 2F4U on 2011-09-05
Just tried to find the package on 11.04 since I don't have 10.04 at hand and the output is as follows:

```
sudo apt-cache search gnome-core
gnome-core - The GNOME Desktop Environment -- essential components
gnome-core-devel - The GNOME Desktop Environment -- development components

```

I am connected to the main mirror. Maybe it helps to change mirrors?

---

