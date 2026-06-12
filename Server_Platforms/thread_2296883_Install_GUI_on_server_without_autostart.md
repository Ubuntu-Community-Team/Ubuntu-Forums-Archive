---
title: "Install GUI on server without autostart"
date: 2015-09-29
forum: Server Platforms
---

### Post by Robert Finley on 2015-09-29
I want to be able to manually start a GUI when I hook peripherals to a headless machine but otherwise have it continue to boot and function as a server.

---

### Post by oldfred on 2015-09-29
You can install just the gui of your choice without installing all the applications.

Lightweight Desktop environment
Ubuntu Server + lxde
works smooth in under 256mb ram on a p2
sudo apt-get install lxde
Or Xfce GUI without any of the associated Xubuntu applications
sudo apt-get install xfce
Comparison of desktop environments 
[https://wiki.archlinux.org/index.php/Desktop_Environment](https://wiki.archlinux.org/index.php/Desktop_Environment)
[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)
Minimal gnome
sudo apt-get install lightdm gnome-terminal synaptic && sudo apt-get install --no-install-recommends gnome-session-fallback

Then you will want to set grub to boot without gui or in text mode.
       Uncomment #GRUB_TERMINAL=console from /etc/default/grub
[http://ubuntuhandbook.org/index.php/2014/01/boot-into-text-console-ubuntu-linux-14-04/](http://ubuntuhandbook.org/index.php/2014/01/boot-into-text-console-ubuntu-linux-14-04/)

---

### Post by Robert Finley on 2015-09-30
Thank you, fixing GRUB is exactly what I was looking for.

---

