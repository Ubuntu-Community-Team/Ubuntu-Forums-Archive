---
title: "ubuntu-server and xorg"
date: 2007-12-23
forum: Server Platforms
---

### Post by ottothecow on 2007-12-23
I am trying to install xserver-xorg-core onto a fresh installation of gutsy-server.

This works just fine on dapper-server (apt-get install xserver-xorg-core xterm) and startx will pop up an xterm.

On gutsy I get a 
Fatal server error:
No valid FontPath could be found.

---

### Post by FakeOutdoorsman on 2007-12-23
Do you have **xfonts-base** installed?

---

### Post by ottothecow on 2007-12-27
If I manually install the xfonts, everything works

my question is why the xorg packages don't work out of the box (like they did in past ubuntu versions).  This seems to be a problem...the xfonts packages are required for the xserver to start so shouldnt they be a part of the meta-package?

---

