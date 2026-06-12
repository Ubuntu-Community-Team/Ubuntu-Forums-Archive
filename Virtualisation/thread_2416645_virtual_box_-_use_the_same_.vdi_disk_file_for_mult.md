---
title: "virtual box - use the same .vdi disk file for multiple virtual machines"
date: 2019-04-12
forum: Virtualisation
---

### Post by marchello_lippi2 on 2019-04-12
Hi all, 
My question is about virtual box - can I use the same .vdi disk file for multiple virtual machines (not simultaneously)?
I will explain. 
I need to install different stuff and it takes time. 
Then I need to backup my .vdi and use it for multiple virtual machines, version0001, version0002 and so on. 
I don't want to start from scratch as I will just waste my time.
So.. any suggestions on how to do it properly? 
I'm in process of installing now. Then I will backup my .vdi and try it.

Upd: it is simple... I just cloned original machine in virtualbox... seems no manual backup of original .vdi is needed.

---

### Post by TheFu on 2019-04-12
Happy you found a working method.  Please mark this thread and aother others as SOLVED using the Thread Tools button to help out the rest of the community.

Might want to checkout snapshots with vbox.  Don't use them too much, not too many layers, because there are performance impacts, but a few layers should be fine.

Cloning a VM is possible using **vboxmanage** CLI tool. Or you can just power down the VM and use the File --> Export Appliance option.  Or simply copy the .VDI file, but then you'll need to setup the VM manually. It is it Windows, it needs to be exactly the same. Linux is much more forgiving, so "Pretty close" is almost always sufficient.  Best to be very careful if there are proprietary drivers.

If you want to build a fresh install and have settings and packages easily installed, might want to check out **apt-mark showmanual**. Save that output to a file.  On another system, a base install, you can use **apt-mark install < file** to feed in that list of packages to be marked for install, then use **apt-get -u dselect-upgrade** to install them all - 2 commands.  Pretty great when you need to move to a new release.  Another tool option for your toolkit.  In the old days, we'd use dpkg --get-selections , but it makes a list of all the installed packages, not just those manually installed.

Options.  You get to pick the best for the situation.

---

### Post by marchello_lippi2 on 2019-04-13
Thanks TheFu. It's rocket science for me so far. I would stick to just cloning machine using VirtualBox interface for now.

---

