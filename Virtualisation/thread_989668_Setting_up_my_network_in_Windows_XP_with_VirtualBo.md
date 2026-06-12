---
title: "Setting up my network in Windows XP with VirtualBox"
date: 2008-11-21
forum: Virtualisation
---

### Post by J03y on 2008-11-21
Hello, When I installed Windows XP with virtualbox I tried connecting to the internet but failed. Since I'm still a noob with virtual machines and all, my question is how do I setup the network so I can have internet connection with Windows XP. :confused:

---

### Post by xcesarfrancox on 2008-11-21
You have to check out the settings of your virtual machine

When you open VirtualBox you can see a list of your machines, select your windows machine, click on settings and go to network on the left menu

You'll see 4 adapters, make sure you have at least one of them enabled (by checking the "enable network adapter" box) and set it to use NAT on "Attached to", you can try different adapters from the list "AdapterType" if the default does not work.

---

