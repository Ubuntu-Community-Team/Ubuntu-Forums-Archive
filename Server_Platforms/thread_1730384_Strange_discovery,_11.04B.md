---
title: "Strange discovery, 11.04B"
date: 2011-04-16
forum: Server Platforms
---

### Post by ingeva on 2011-04-16
After an upgrade or new installation I run a few scripts to make sure everything is installed and in order.
These scripts refer to the $HOME directory, but need to run as root (sudo).

When these scripts are executed, 11.04  thinks the $HOME directory is /root, so things that were intended for the $HOME directory end up in the wrong place.
This may be the reason why my desktop menus have become impossible to use (Haven't tested that yet, but I have to fix and repeat the whole procedure anyway).

Of course it's easy to fix, but I would like to ask if this is a bug, or is it per design?

---

