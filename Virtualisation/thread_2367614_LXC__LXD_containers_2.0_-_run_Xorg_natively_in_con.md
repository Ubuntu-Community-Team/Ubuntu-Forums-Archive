---
title: "LXC / LXD containers 2.0 - run Xorg natively in container"
date: 2017-08-01
forum: Virtualisation
---

### Post by kbs1 on 2017-08-01
Hello,

I am looking for a solution to run full Xorg environment in a container. The use case is this:

I enter an container using lxc exec u1 bash, then type startx. I expect X will normally start and I can view full native graphics desktop with acceleration (youtube videos, etc) as if it was running on the host itself.

Is there any way I can achieve this? All tutorials on the internet are outdated or not working, with various issues. I'd like to keep this as simple as possible. Currently startx gives me:
parse_vt_settings: cannot open /dev/tty0 (no such file or directory).

Use case: normal root in container, I install / update my system based on my preferences, and THEN, I can sync (clone) my container to another machine, make snapshots before big upgrade, and so on. Primary target of usecase: I have 3 locations where I work, shifting between them, and I want my desktop environment updated, so for example if I configure SeaMonkey to my liking, upgrade PHP, get a new project going, anything, I don't want to do that 3 times, and just sync the container.

I currently use FreeBSD for this, see [https://github.com/kbs1/freebsd-synced-xjails](https://github.com/kbs1/freebsd-synced-xjails) , but I'd like to start using Linux again.

Thank you very much! ;-)

Best Regards,
Viliam :)

---

### Post by bmullan2 on 2017-08-08
this should help...

I've tried doing it and both the gui and audio worked.

[https://blog.simos.info/how-to-run-graphics-accelerated-gui-apps-in-lxd-containers-on-your-ubuntu-desktop/](https://blog.simos.info/how-to-run-graphics-accelerated-gui-apps-in-lxd-containers-on-your-ubuntu-desktop/)

However, that would be applicable to 1 machine because of the device mapping.

You could install x2go ([www.x2go.org](www.x2go.org)) and that works well with containers.   Install the x2goserver and x2goserver-xsession in the container and the x2goclient in the "host"

---

