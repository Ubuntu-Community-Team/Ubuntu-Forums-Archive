---
title: "Installing from a virtualized image, possible?"
date: 2009-03-27
forum: Virtualisation
---

### Post by bstpierre on 2009-03-27
I would like to install and configure Ubuntu in a VM (most likely VirtualBox using Windows XP as a host) and when the configuration is complete, use the virtual HD image to install to my actual system.

Is this possible? Does a guide exist showing how to do this?

Besides the display drivers and the Xorg configuration, should I expect other issues when moving the installation over?

The reason I am doing this is to replace a Windows 2003 server with minimal down time. I'd like to configure postfix, svn, apache, MySQL, etc., and test it before deploying.

---

### Post by Jose Catre-Vandis on 2009-03-28
The problem is that the virtual hardware will be different from your actual hardware, so ubuntu will just not be configured on installation in the same way. You can do what you suggest, byut you will most likely have a lot of fun reconfiguring ubuntu to all your hardware, and quite possibly a lot of your software installation too?

What you could do is at least work out all the configurations you need, and simply copy these over when you do the real install.

Alternately, if your server is up to it, install VBox on the server, set up your new server as you want, and then leave it there as a virtual server :)

---

