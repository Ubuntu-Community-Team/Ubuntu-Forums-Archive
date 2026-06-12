---
title: "Installing game server package opens up vulnerabilities?"
date: 2008-05-14
forum: Security
---

### Post by Sarah L on 2008-05-14
Hi,
Several months ago, I decided to try out the multiplayer game Tremulous, and being a Linux newb, I opened up the package manager and installed every package with the search term in it. Unfortunately, I selected the tremulous-server package as well, and I had that installed until recently.

I hear that the server package tries to make your system a dedicated server and runs at startup. Does this open up the system to outside intrusions? If so, what are the chances that this hole was exploited and how can I resolve the issue?

Thanks!

By the way, I've reformatted my computer since, but I had sensitive files stored in my home directory during the previous install... any chance those got stolen?

---

### Post by Dr Small on 2008-05-14
Unless the Tremulous server package has a gaping hole in it (which I highly doubt if it is anywhere popular), then you are just jumping at shadows. To completely reformat the drive, you must be very paranoid.

All you needed to do, was uninstall the server package and remove the startup files. Besides, unless you opened a port that this server runs on (and if you are behind a router, that one too), I don't think anyone could have gotten in to exploit the package.

Dr Small

---

