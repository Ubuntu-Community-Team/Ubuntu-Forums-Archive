---
title: "How to install fluxbox in gutsy server?"
date: 2008-03-07
forum: Server Platforms
---

### Post by techno-wiz on 2008-03-07
I have a fresh gutsy server installation and want to use fluxbox for my gui. I did:

sudo apt-get update
sudo apt-get install fluxbox

and followed with a reboot. It is still coming up in the command line and after logging in I type fluxbox. It says "Couldn't connect to Xserver"

What else do I need to install/configure to get it to come up on fluxbox? Is there a simple way to install this like the install ubuntu-desktop does for gnome?

---

### Post by eriqjaffe on 2008-03-07
Yeah, Fluxbox won't run without xorg.

```
sudo apt-get install xorg
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by kerry_s on 2008-03-07
for X always install "xorg" it looks like this.

**sudo apt-get install xorg fluxbox**
i'll use this
**sudo apt-get install xorg synaptic fluxbox rox-filer leafpad mc**
**sudo update-menus ** <-might have to install "menu", can't remember if it's still a part of fluxbox.
**startx**

**leafpad ~/.bash_profile**

[B]if [ `tty` = "/dev/tty1" ]; then
startx
fi
[/B]
will startx when you log in to tty1

**sudo apt-get install rungetty**

**sudo leafpad /etc/event.d/tty1**

comment out->
**respawn /sbin/getty 38400 tty1**

put->
**respawn /sbin/rungetty tty1 --autologin user**

"user" would be your log in name.

should auto log you in.

---

### Post by techno-wiz on 2008-03-07
That did the trick. Thanks!

---

