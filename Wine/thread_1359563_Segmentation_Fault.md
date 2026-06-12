---
title: "Segmentation Fault"
date: 2009-12-19
forum: Wine
---

### Post by steinb on 2009-12-19
I am using WINE on two different PCs run Ubunut 9.04 Jaunty. Wine was working fine until a kernel update. 

Now when I start a Wine program (like notepad), I get Segmentation fault.

Am I the only one having the problem? Does anyone know how to fix it?

---

### Post by beastrace91 on 2009-12-19
Wine version? Post the output from terminal please when the program dumps? Also have you tried reinstalling Wine? 

~Jeff

---

### Post by steinb on 2010-01-02
steinb@Ubuntu-i386:~$ wine --version
wine-1.1.35
steinb@Ubuntu-i386:~$ wine notepad
Segmentation fault
I don't know how to generate any other data.
I did completely remove Wine and the Wine home directory and reinstall. That did not help. I have a NVIDIA driver. I switched to a VGA video driver. That did not help.
I did boot using a older kernel and WINE worked.

---

