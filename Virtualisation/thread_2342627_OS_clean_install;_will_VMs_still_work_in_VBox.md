---
title: "OS clean install; will VMs still work in VBox"
date: 2016-11-08
forum: Virtualisation
---

### Post by ajgreeny on 2016-11-08
I am about to clean install 16.04 over my 14.04 main installation of Xubuntu.
I have a separate /home partition with all my current VMs, eight of them, all of which run beautifully, sitting in the default **~/VirtualBox VMs** folder and all the config files of VBox in the **~/.config/VirtualBox** folder.

Can any of you experts in VBox tell me whether these VMs will be found and run when I install virtualbox in the new 16.04 Xubuntu installation, or do I need to export each VM first to an ova and then import each ova back into the new VBox installation.  I intend to use the same version of VBox-5.1.8.

I have one or two VMs that are essential to me and must not lose the ability to continue running them, hence my question before starting the move to Xubuntu-16.04.

---

### Post by &amp;KyT$0P# on 2016-11-08
Yes they will work.  You just need to double-click each VM's .vbox file to get VirtualBox see it, if it doesn't already.

---

### Post by Habitual on 2016-11-09
I've had
```
13G    VboxVMs/Dokuwiki
9.2G    VboxVMs/Windows
```
for about 5 years now.

---

### Post by ajgreeny on 2016-11-09
Thanks folks.

I added a partition and dual booted 14.04 and 16.04 just in case I didn't manage to get the VMs working as I needed, but they all worked great.  THe one problem I nearly forgot was to add me to the vboxusers group in 16.04 without which the USB devices would not connect. Sorted that and all now working just like in 14.04.

---

### Post by C.S.Cameron on 2016-11-10
I keep a Win 10 VM on a flash drive as a backup.
I can copy it to other computers or run off the flash drive
A 1 or 2 minute install on most computers that have Vbox.

---

### Post by Habitual on 2016-11-10
> **ajgreeny said:**
> Thanks folks.

I added a partition and dual booted 14.04 and 16.04 just in case I didn't manage to get the VMs working as I needed, but they all worked great.  THe one problem I nearly forgot was to add me to the vboxusers group in 16.04 without which the USB devices would not connect. Sorted that and all now working just like in 14.04.
As a precaution, I also suggest periodic exportation of high-value appliances in Virtualbox.
These export to .ova and are usually quite small in comparison to a full-fledged file copy.

Good Luck!

---

