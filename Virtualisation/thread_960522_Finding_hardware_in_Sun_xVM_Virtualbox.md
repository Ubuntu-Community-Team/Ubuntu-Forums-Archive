---
title: "Finding hardware in Sun xVM Virtualbox"
date: 2008-10-27
forum: Virtualisation
---

### Post by Gennn89 on 2008-10-27
Need help recognizing my wireless and audio hardware in vista virtual. also would be nice to know how to download my programs on linux and then play them on windows without doing something time consuming like burning discs. thanks

---

### Post by forger on 2008-10-27
In virtualbox, by default, the guest o/s uses the host o/s internet and it you shouldn't have any problems.. In the guest operating system Settings > Network, try **Adapter Type** as "PCnet-PCI II" or "PCnet-FAST III", also set **Attached to** as "NAT".

You can also set up a shared folder between linux (host) and windows (guest), in Settings > **Shared Folders**. Note that for this to work you need to install the virtualbox additions in the guest o/s (once your windows is booted up and you are logged in, go to menu Devices > **Install virtualbox additions**).
[COLOR="Red"]Virtualbox additions are available if you **download virtualbox from their site**[/COLOR]: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

The manual has more information about setting up shared folders: [http://download.virtualbox.org/virtualbox/2.0.4/UserManual.pdf](http://download.virtualbox.org/virtualbox/2.0.4/UserManual.pdf) (or [here]("http://www.virtualbox.org/wiki/Downloads#Usermanual"))

---

