---
title: "vbox guest additions changes window to 800x600"
date: 2010-01-15
forum: Virtualisation
---

### Post by akn0taw on 2010-01-15
Good day,

On my Koala system, I installed Virtualbox OSE. I used an installation of windows 7 rc that I had earlier tried with Hardy's VirtualBox. With the Koala version, I'm now able to access the network.

However, when I tried to install the guest additions provided by ubuntu, the monitor screen size dropped to only 800x600 and could not be changed. Without the guest additions, I have 1024x768 but don't have shared folders.

How can I fix the screen size problem or how can I set-up shared folders only?

ak

---

### Post by Perryg on 2010-01-15
Once the guest additions are installed you use the mouse click and drag to change the screen size or the host+f toggle to go in and out of full screen.  Does this not work for you?

You must have the guest additions installed to be able to use the shared folders.

---

### Post by fouadatmeh on 2010-01-15
you can also press Ctrl+g to resize the guest OS to VirtualBox's window size..
(there is an option in the "machine" menu that will do this for you everytime you resize vbox's window)

---

### Post by akn0taw on 2010-01-19
Guest additions had been installed. Afterwards, I changed the Win 7 video driver to standard vga and I could once again get a 1024x768.

ak

---

