---
title: "directx"
date: 2009-02-06
forum: Wine
---

### Post by skipsy on 2009-02-06
hi im nu to all this and dont really know what im doing can some 1 please tell me what this means and how to do it: install a native mscoree.dll and streamci.dll into /system32 from a windows install and set them to native Windows.

---

### Post by cogadh on 2009-02-06
You don't need to install DirectX, Wine already has its own implementation of DirectX that should work just fine (in most cases). 

However, if you are still going to do that, what that instruction is telling you is to copy the mscoree.dll and streamci.dll from the system32 directory on a Windows machine into Wine's system32 directory (found in the /home/<username>/.wine/drive_c/windows directory). After copying those DLLs over to Wine, you need to run winecfg, go to the Libraries tab and apply an override for each of them (fairly self-explanatory once you get there). You will need to set each of the overrides to "Native" instead of "Built-in", so that Wine knows to use the Windows native DLL you copied, instead of Wine's own built-in implementation.

---

### Post by skipsy on 2009-02-06
thanks mate been big help 1st time since i started on ubuntu that i relay understoodwhat was said  cheers :D

---

