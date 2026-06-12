---
title: "Ubuntu black screen with cursor - Nvidia graphics issue on Hyper-V VM"
date: 2021-03-05
forum: Virtualisation
---

### Post by connersz on 2021-03-05
[COLOR=#242729][FONT=Arial]I have Ubuntu running on a Hyper-V as a VM which I set up on my PC before moving to a new server to work as a web server.

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The Ubuntu VM loads fine but where the desktop should be, all that shows is a black screen and black cursor.

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]After looking online. It looks as though this is a graphics issue, caused by the change in graphics adapters and Ubuntu not automatically updating them.

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I've tried several things including pressing "e" on startup and adding nomodeset and nouveau modeset=0 in the appropriate places but it had no effect.

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I cannot access anything that requires keyboard shortcuts due to Ubuntu running on Hyper V.

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]All of the online articles that I found referenced making changes to files or using the terminal, both of which I can't do due to the screen being blank.

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]There are two recovery modes listed in grub, but neither do anything. They just reload the menu when selected. There's another entry in grub for EUFI firmware settings. I'm not sure what that's for but it also does nothing.

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Please help me. I'm losing the will to live working on this![/FONT][/COLOR]

---

### Post by lammert-nijhof on 2021-03-08
I also get a black screen when loading Ubuntu in full screen.I have two solutions that work with Virtualbox. Start the VM in a windows and not in full screen or else if loaded a and when on the black screen use the hypervisor to toggle full screen off and on.

---

