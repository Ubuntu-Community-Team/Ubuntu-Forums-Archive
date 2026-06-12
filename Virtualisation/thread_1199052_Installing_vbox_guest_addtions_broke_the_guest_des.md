---
title: "Installing vbox guest addtions broke the guest desktop."
date: 2009-06-28
forum: Virtualisation
---

### Post by xl_cheese on 2009-06-28
I installed vbox guest addtions and then was prompeted to restart.  I did and now it will only boot to a command line login.

I've wasted too much time trying to figure this out.  Hopefully someone here can help me.

I'm using a ubuntu host and wanted to try out Kubuntu in the guest.  Everything seemed to be working fine until I installed the guest addtions.

Thanks.

---

### Post by bodhi.zazen on 2009-06-28
reconfigure X in the guest.

Easiest if to simply move the /etc/X11/xorg.conf to a back up.

sudo mv /etc/X11/xorg.conf /etc/X11/sorg.conf.backup

then re-boot.

The guest additions do not like or need any customizations to xorg.conf.

---

