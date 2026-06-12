---
title: "Ubuntu Server vs. Desktop"
date: 2010-10-29
forum: Server Platforms
---

### Post by ICEB3AR on 2010-10-29
Hey there,

I'm planning a server which should serve especially a LTS, fIrewall, NFS and Print. 
Some time ago I configured a LTS on basis of ubuntu 8.04 server. The following way:
- install ubuntu 8.04 server edition
- install ubuntu-desktop via apt-get
- install and configure needed software for LTS
- build client
I tried the same with 10.04, but there where some side effects when installing ubuntu-desktop on top of the server-basis e.g. some missing applets in the panel and sometimes the X-server is gonna break for some seconds or some warnings appear.

That's why the following questions came to my mind:
What would be the better basis for the LTS?
What is the exact difference between the server-kernel/edition and the desktop-kernel/edition? Is there any? (It is self-explaining, that the desktop-edition has packages included like gnome and openoffice e.g.)
What shoudl I use for the above demand?

Best regards and thanks for any answer
ICEB3AR

---

### Post by arrrghhh on 2010-10-29
If you need GNOME or ubuntu-desktop, then by all means just install Ubuntu-Desktop.  The whole point of the server distro is to be lean&mean, so no X, GNOME, desktop environments, etc.  If you feel you need this, just install ubuntu-desktop - you can run ALL the same services as you can with ubuntu-server, so you're not missing out on anything.

The 32-bit server kernel has PAE support, not sure about the desktop kernel.  This only applies if you want to run a 32-bit OS, but have more than 4gb of RAM.

If you want more information on Ubuntu Server & GUI's - see the official doc on [ServerGUI](https://help.ubuntu.com/community/ServerGUI)

---

### Post by dtfinch on 2010-10-29
The server kernel defaults to the deadline scheduler instead of CFQ, has kernel preemption (where device drivers or the kernel itself can be interrupted, to sometimes improve desktop app responsiveness at a cost to overall performance) turned off, and has a lower timer resolution. Not sure what other differences there are.

[https://help.ubuntu.com/10.04/serverguide/C/preparing-to-install.html#intro-kernel-diffs](https://help.ubuntu.com/10.04/serverguide/C/preparing-to-install.html#intro-kernel-diffs)

---

