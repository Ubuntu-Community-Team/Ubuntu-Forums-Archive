---
title: "vmware after ubuntu 8.04 upgrade help"
date: 2008-03-17
forum: Virtualisation
---

### Post by ringeerdance on 2008-03-17
I recently updated to the latest alpha release of Ubuntu (Gutsy), everything works except for VMware server.  any help would be greatly appreciated

---

### Post by MetalMusicAddict on 2008-03-17
The kernel modules have most likely not been updated yet. Only thing you can do is compile your own.

Personally, I've switched to VirtualBox.

---

### Post by fjgaude on 2008-03-17
Find the config file and run it:

```
sudo /usr/bin/vmware-config.pl
```

That is all that is required to "compile the kernel".

There is a chance that the .pl file is not in /usr/bin. You can find it with the locate command:

```
locate vmware-config.pl
```

Let us know how you are doing.

---

