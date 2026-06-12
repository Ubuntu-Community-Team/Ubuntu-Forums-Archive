---
title: "xen kernel e gdm segment fault on ubuntu 7.10"
date: 2008-01-28
forum: Virtualisation
---

### Post by nisp on 2008-01-28
Hi all !

I've just terminated an upgrade to ubuntu 7.10 from 7.04 and no apparent problems have arisen on my Dell/32 bit system.
Then I've installed (synaptic) packages to run Xen 3.1 resulting in kernel 2.6.22-14--xen. But when I restart my machine, gdm fails to start and I cannot consequently login. If I restart gdm it goes in Segment fault :-(

/etc/init.d/gdm restart =>

/etc/init.d/gdm: line 49: 5486 Segmentation fault (core dumped) start-stop-daemon --start --quiet --oknodo --pidfile $PIDFILE --name $SSD_ARG --$CONFIG_FILE > /dev/null 2/&1

I checked in case and gdm is at its newest version. Running kernel 2.6.22.14-generic all is ok and gdm starts perfectly.

Does anyone have ideas about this ?

Thanks a lot in advance !!

---

### Post by fanatik on 2008-02-03
I have something similar, possibly.

I am running 7.10 64-bit version desktop and installed xen via apt, when I boot into the xen kernel just before the login screen appears i get the caps lock and the scroll lock lights flashing at me -- kernel panic? :(

I can't tell yet what is causing this, but it could be gdm as per your post above... I don't yet know how to debug it or work around it.... perhaps I could boot to a command line and see if that works. I don't know yet. I am tempted to uninstall xen and install from sources, but that might be more trouble than it's worth.

if anyone has any ideas, I will try any suggestions.

Thanks!

---

### Post by fanatik on 2008-02-03
OK that was due to me using nvidia drivers, I reverted to nv and all was well. sorry i can't be of more help with your gdm problem though...

---

