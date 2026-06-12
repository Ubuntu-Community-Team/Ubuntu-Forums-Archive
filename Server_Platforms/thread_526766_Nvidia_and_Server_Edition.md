---
title: "Nvidia and Server Edition"
date: 2007-08-15
forum: Server Platforms
---

### Post by infinitezero on 2007-08-15
I was unable to install Nvidia on the 7.04 server edition and and wondering if anyone had any thoughts?

I have tried every method on the forum and even the auto install by tseliot. I have been a Linux user for a while now and never have I had video driver kick my back side so badly, any help would be greatly appreciated.

Thanks,
iz

---

### Post by ssam on 2007-08-16
I take it you mean the propreitary Nvidia graphics driver.

the server edition is exactly the same as the normal edition, only with less packages installed by default. For example there is no X server by default.

If you want the Nvidia driver, then i assume you want a graphical desktop, and to run 3D applications. do you have any particular reason to use the server edition if this is what you want?

if you want a graphical desktop, then at the very least you will need to install
xserver-xorg

to transform your install into a full desktop edition you can install
ubuntu-desktop

---

