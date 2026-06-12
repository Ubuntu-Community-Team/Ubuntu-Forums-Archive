---
title: "Tails guest needing guest additions? (Kubuntu host)"
date: 2013-04-14
forum: Virtualisation
---

### Post by Stonecold1995 on 2013-04-14
I just upgraded from Tails 0.17 to 0.17.2.  However now when I boot from the iso in VirtualBox, the mouse is jumpy and sometimes vanishes, and simply acts strangly.  This same thing happens with Kubuntu, Fedora, and Debian when they're installed through VirtualBox without guest additions installed.  But why should the update from 0.17 to 0.17.2 suddenly require (I presume) the guest additions?

How do I prevent the jumpy cursor when running Tails 0.17.2 in a Kubuntu host?

---

### Post by theherk on 2013-04-16
I do not have the solution, but I can confirm that I have seen exactly the same behavior. I do not know what is different.

---

### Post by Stonecold1995 on 2013-04-18
> **theherk said:**
> I do not know what is different.
I'm guessing whatever is responsible for reacting to the presence of a virtual machine is either absent or broken.  It seems that Tails detects that it's virtualized, but is unable to adjust settings accordingly.

On a related note, another problem is that automount does not work anymore, so I know it's not just a problem with the mouse, it's a problem with the virtual machine-related software.

---

### Post by walfra4 on 2013-06-02
There is no need to install the guest additions - for me (using Xubuntu 12.04) following worked:
Change under "General" the OS-Type to Windows XP - the mouse now moves smoothly (only in full-sreen-mode but not in the scale-mode)!

Hope this helps!

---

