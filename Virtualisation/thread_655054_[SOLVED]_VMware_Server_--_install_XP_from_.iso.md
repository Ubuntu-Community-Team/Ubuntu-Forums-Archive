---
title: "[SOLVED] VMware Server -- install XP from .iso?"
date: 2007-12-31
forum: Virtualisation
---

### Post by A-dogg on 2007-12-31
virtualbox allows you to install from a disk image. can you do that in vmware? for some reason, when I try to install from my xp disk in vmware, it takes hours to do what should take 30 minutes. No idea why...

thanks!

---

### Post by fjgaude on 2007-12-31
I'm not sure what you mean by .iso install... you can have an .iso disk to install things in vmware, but I'm not sure if you can do it with Windows.

I used by Microsoft install disk and it took the normal about of time as if I was installing into a regular partition.

Does this help:

[http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html)

So many things to take into consideration.

---

### Post by A-dogg on 2007-12-31
i was asking if I'm install vmware server on gutsy and want to install xp into vmware, can I tell vmware to install off of an xp.iso or can I only do it from my actual xp disc? I tried to do it from my disc but it was excruciatingly slow...

regarding that link... I looked at it... when i install vmware server, I didn't do any of that terminal stuff... I just downloaded the latest version from synaptic (which is the latest stable version from the vmware website). Not sure why that guy said to do it via the terminal and compiling the version from source...

thanks.

---

### Post by fjgaude on 2007-12-31
Most folks have installed from their xp disk from MS.

---

### Post by scxtt on 2007-12-31
i've installed windows off an .iso ... as long as the .iso doesn't have any issues, like it isn't bootable, it should be fine ... i've done it 2 or 3 times w/ vmware server ...

---

### Post by A-dogg on 2007-12-31
scxtt,

could you tell me how you do that in vmware server? it was easy to see in vbox, but i can only see how to boot/install from an actual cd in vmware...

thanks!

---

### Post by scxtt on 2007-12-31
edit the vm's cd-rom settings to look like this (just use browse to find the .iso file after you've created a basic VM, w/ no OS yet):

---

### Post by A-dogg on 2007-12-31
exactly what I needed -- thanks!!!

---

