---
title: "can VMware Server be run from the command line?"
date: 2008-06-11
forum: Virtualisation
---

### Post by tha_toadman on 2008-06-11
I have a system that I've installed 7.04 Alternate on (command line system) and then got VMware Server installed as well. Is it possible to run this program/configure a new OS from the command line or do I need a GUI? I'm thinking I do as every guide I've come across in the past 2 days looks to be running Gnome in it.

I'm trying a minimalist approach with very little overhead, if possible. If I do have to run a GUI, then I'll most likely run XFCE since it's pretty light.

Thanks!

---

### Post by fjgaude on 2008-06-12
AFAIK, yes a GUI is required for vmware products. I'm sure just about any of them, GUIs that is, will work.

---

### Post by tlacuache on 2008-06-12
VMWare Server can be run without a GUI, but you'd have to run the GUI client (vmware-server-console) on another machine to manage it, create VMs, etc.

For example, I ahve VMWare Server running headless on a CentOS 5 box in my basement which doesn't have X or anything installed on it, then I manage it with vmware-server-console on my Ubuntu desktop.

However, if you've only got a single machine, you'll have to install vmware server as well as vmware server console and connect locally to localhost (127.0.0.1). In that case, you'd have to have some sort of window manager installed. You could install xubuntu, it's pretty lightweight.

---

