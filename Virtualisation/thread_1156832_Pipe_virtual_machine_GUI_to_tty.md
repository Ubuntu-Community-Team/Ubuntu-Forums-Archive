---
title: "Pipe virtual machine GUI to tty"
date: 2009-05-12
forum: Virtualisation
---

### Post by chocblu on 2009-05-12
HI All,

Im setting up a desktop with ubuntu, but as a developer i need to have access to windows as well.

What id like to do is to have a a virtual machine running (windows XP), and by pressing one for the function keys plus alt-ctrl i can switch to the GUI. like when you have multiple consoles and switch back and forth between them?

Is this possible?

thanks for any help.

Mark

---

### Post by HermanAB on 2009-05-12
Howdy,

The standard way to control Windows is with rdesktop.

Enable RDP in the Windows VM and then let it run in the background.  Use rdesktop to connect to it.

---

