---
title: "VirtualBox user group deletion"
date: 2009-11-02
forum: Virtualisation
---

### Post by Sherlock Holmboy on 2009-11-02
I was trouble shooting the USB issue with the OSE flavor of VirtualBox, during which I created a user group "vboxusers". I later uninstalled and installed the non-free version. During the install there was an error that vboxusers was already exists and was a non-system group. I was trying to delete the group through the administrative application in the system menu, but it keeps reapearing in the list if I reopen the application. How do I manually remove this group?

---

### Post by Sherlock Holmboy on 2009-11-02
got it:

sudo groupdel

---

