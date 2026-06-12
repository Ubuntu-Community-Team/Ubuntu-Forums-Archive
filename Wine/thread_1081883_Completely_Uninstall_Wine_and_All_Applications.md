---
title: "Completely Uninstall Wine and All Applications"
date: 2009-02-27
forum: Wine
---

### Post by jfinner1 on 2009-02-27
I tried to find the answer to this, but I kept getting half answers, or segmented answers. Truth is, I'm not too good at Linux yet, and I really need a step-by-step. Here's the issue: I tried to install a game with Wine. It didn't work. I found out that it didn't work because of something stupid I did, but because of that I needed to reinstall the program. But when I went to uninstall it, I got all these errors, and and when I went to reinstall I got more errors. So I figure that if I uninstall Wine, I can start over. But, I've read that just uninstalling Wine from synaptic won't remove the installed applications, and therefore won't help me at all. So, I figure if I completely remove Wine and all traces of all installed applications, and then install Wine again, it will be like starting from scratch. But, I don't know how to do that.
So could someone please tell me step-by-step how to completely remove Wine and all traces of the installed applications? Thank you very much.

---

### Post by kidux on 2009-02-27
You don't need to re-install WINE. Just go into your /home directory, hit [ctrl]+h if you don't see any files preceded by a . and find the .wine directory, then delete it. Next time you run WINE, it will setup that directory again and you can then install the program you wanted.

---

### Post by jfinner1 on 2009-02-27
That seems to have worked. I'll know if it's completely fixed of not in a few minutes. Thanks!

---

### Post by cogadh on 2009-02-27
Just a quick explanation of what kidux just told you to do:

When you first run Wine, it creates the .wine directory in your home folder. This directory is actually Wine's "fake Windows" drive. Basically its what Wine uses to fool a Windows program into thinking it is on a Windows machine, plus it includes all of Wine's settings. If you look at what is in the directory, you will find Wine's version of the Windows registry, as well as subdirectories that contain references to your hardware and Wine's version of the Windows "C:" drive. When you install anything with Wine, it is actually installed to this directory (by default). 

The Wine "program" (i.e. all its binaries) actually resides in a completely different directory (/usr/bin/wine I think, not at my Ubuntu machine right now) and is not touched at all by anything you install with Wine. Because of this simple yet brilliant way Wine is designed, you can beat, crush, torture, burn and in every way abuse Wine with Windows applications without ever fearing damage to Wine itself. If you manage to royally screw everything up to the point where you can't get Wine to work anymore, you can just delete the .wine directory and Wine is restored to its default functioning state (of course you also lose any Windows apps you installed).

---

