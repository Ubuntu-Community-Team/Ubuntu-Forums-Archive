---
title: "VirtualBox and network"
date: 2008-08-27
forum: Virtualisation
---

### Post by vcnz on 2008-08-27
On my notebook (8.04 desktop) I've installed the last VirtualBox version.

I've a wireless connection and an ethernet wired connection, both works fine (one per time)

On my host I run as a guest host for test, another 8.04 desktop, using the live cd version.

Is it possible to use the wireless connectione for the host and the wired connection for the guest host?

If no, how can I do to use the network only on the guest host?

Thank you

---

### Post by Jose Catre-Vandis on 2008-08-27
As far as I know, Virtualbox have not yet implemented the use of wireless connections from a guest through a host. however you can overcome this by masquerading your guest's IP. Instructions on how to do this are found here:[http://bimma.me.uk/2007/09/30/ubuntu-creating-host-interface-networking-for-virtualbox/](http://bimma.me.uk/2007/09/30/ubuntu-creating-host-interface-networking-for-virtualbox/) (scroll down a bit for the masquerading howto)

---

### Post by vcnz on 2008-08-28
Thank you,

just I enabled the wired network on a virtual host and the wireless on the host. 
I enabled bridging from both networks. It works!!!
Thank you

---

### Post by astabeno on 2008-08-28
I had Virtualbox and Wireless working fine, for a while.  I then moved my laptop to another network where I had to set a static IP and now my wireless does not work at all. I was using a network bridge with VBox Interface to do bridged networking.  In order for that to work after a reboot I have to edit my the bridge info out of the interface file, then restart my machine, then edit the bridge info back in the restart networking, then read the VBox interfaces.  Then everything works, until I reboot.  I have been doing this a while and its and I would love to get this fixed.

---

### Post by Jose Catre-Vandis on 2008-08-29
@ astabeno

Have you tried the masquerading trick?

---

### Post by astabeno on 2008-08-29
> **Jose Catre-Vandis said:**
> @ astabeno

Have you tried the masquerading trick?

No how do I do that?

---

### Post by Jose Catre-Vandis on 2008-08-30
> **astabeno said:**
> No how do I do that?

See my previous post in this thread for link

---

