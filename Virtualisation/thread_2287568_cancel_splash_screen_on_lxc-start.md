---
title: "cancel splash screen on lxc-start"
date: 2015-07-20
forum: Virtualisation
---

### Post by odror on 2015-07-20
I have created a container with the mate-desktop.

when I initiate it with lxc-start or stop it with lxc-stop I get the [ubuntu]-mate splash screen.

I thought that the splash screen is initiated by grub. I thought that the containers are not going through the grub process.

How can I disable the splash screen if it is not initiated by grub.

My real issue is that when I start the ubuntu-mate lxc I loose the keyboard (the mouse is ok). I am guessing that the splash screen and the "takeover"
of vt1 by the container startup process is the cause.

I have to stop the lxc remotely and restart lightdm on the host remotely to have the keyboard back.

Any help will be appreciated.

---

