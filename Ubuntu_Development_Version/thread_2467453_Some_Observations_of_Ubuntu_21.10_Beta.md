---
title: "Some Observations of Ubuntu 21.10 Beta"
date: 2021-09-27
forum: Ubuntu Development Version
---

### Post by Dennis N on 2021-09-27
A few preliminary observations on Ubuntu 21.10. Bugs?  

In Wayland session (but not Xorg), when using the available DMZ White cursor the hot spot is considerably to the left and above the arrow tip making it difficult to work accurately - in particular, text selection and cursor positioning. Other cursors tried have this same problem. Using the "show cursor" option in Universal Access will reveal the actual hot spot. 

It appears after a couple of tests that even if Xorg has previously been selected and indicated as Display manager in login screen options, you need to re-click on "Ubuntu on Xorg" at every login to get the Xorg session after login. For checking on display manager, I switched off the Ubuntu Dock and use Plank. Plank is known to not run in Xorg. It is the canary in the coal mine. If it is not up and visible on the Desktop view after login, I know I'm not on Xorg.

KWrite (Flatpak) window is not resizable in Wayland. It is resizable in Xorg. Also, KWrite (Flatpak) does not use system cursor theme in Wayland. Other Flatpaks might be affected as well if used in Wayland?

Popular Extension "No Overview at Startup" does not work in Ubuntu 21.10 - it does work in other distros (Fedora and Manjaro) with Gnome Shell 40 (this is not Ubuntu's problem to correct). This does not otherwise affect normal operation.


(System: Ubuntu 21.10 beta installed as QEMU/KVM virtual machine)

---

