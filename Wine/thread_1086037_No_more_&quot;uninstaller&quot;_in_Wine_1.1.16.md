---
title: "No more &quot;uninstaller&quot; in Wine 1.1.16"
date: 2009-03-03
forum: Wine
---

### Post by alejobar on 2009-03-03
Hi I just upgrade to the new wine 1.1.16 and theres no uninstaller option anymore, when I go to menu, then Uninstall Program, I get an error saying that cannot be found, I tried typing "uninstaller" in terminal and got the same error that it is not installed and I can run apt get wine to get it, I run that and it tells me that I already have the latest wine available

Anyone with the same problem?

---

### Post by aaronb on 2009-03-03
Try typing "wine uninstaller" in a terminal.

The same issue is present here too, but "wine uninstaller" works from terminal.

---

### Post by alejobar on 2009-03-03
Yes you are right running wine uninstaller works from terminal, I just edit the menu in applications, and change the command from: uninstaller to wine uninstaller, now I can launch it from the menu too :D

---

### Post by YokoZar on 2009-03-04
I'll fix this in the next package.  Thanks.

---

### Post by alex.rayu on 2009-03-04
Why would you need to run wine uninstaller? It's like a parachute on a submarine, does not do anything. Just for your feeling of security.

---

### Post by alejobar on 2009-03-04
Thanks Yokozar! I thought that it was something wrong with Wine and I was going crazy!! hahahha

> **alex.rayu said:**
> Why would you need to run wine uninstaller? It's like a parachute on a submarine, does not do anything. Just for your feeling of security.

Alex, I know its a hit and mis with the uninstaller, it just works with some programs and the other you have to delete the .wine folder to remove them and then take care of the menu entries manually, good thing Wine its getting better and better, I hope soon we will be able to run almost anything in ubuntu.

---

### Post by YokoZar on 2009-03-05
> **alex.rayu said:**
> Why would you need to run wine uninstaller? It's like a parachute on a submarine, does not do anything. Just for your feeling of security.

Wine uninstaller works fine *except* for the menu entries (which, admittedly, are the most visible things).  The actual program will still be uninstalled, however - just like if you went to add/remove programs in windows.

---

