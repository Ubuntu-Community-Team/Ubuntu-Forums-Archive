---
title: "Is it possible to uninstall xgl/compiz?"
date: 2006-10-06
forum: The Cafe
---

### Post by user1397 on 2006-10-06
under dapper, i installed xgl/compiz using this guide: [http://forum.beryl-project.org/viewtopic.php?id=389](http://forum.beryl-project.org/viewtopic.php?id=389)

then i removed the compiz repos, and went to status in synaptic, looked in obsolete, and found the compiz and xgl packages there.  so i removed those too.

then i dist-upgraded to edgy, and now im running edgy beta.  but, if i look in sessions in my gdm, xgl still shows up.  how can i competely remove it?

also, does xgl/compiz/beryl work only on the kernel you installeed it from, or are kernels not a factor when considering xgl/compiz's functionality?

My plan is to uninstall xgl/compiz, and eventually install beryl.

---

### Post by PriceChild on 2006-10-06
SOmeone else asked this exact same question... i ended up acciadently removing his entire xserver and 76 other programs.... check out here:

[http://ubuntuforums.org/showthread.php?t=269667](http://ubuntuforums.org/showthread.php?t=269667)

btw the instructions have been edited and should now work.

---

### Post by slimdog360 on 2006-10-06
I managed to get rid of it, though I cant remember how I did it.

---

### Post by nothingworks on 2006-10-22
I just removed compiz/XGL because my old pc was too sluggish with it.

Steps:
1) uninstall compiz and XGL using Symantic package manager (System->Administration)
2) Make sure you made a backup of your xorg.conf before installing XGL (below I assume it was xorg.conf.backup)
[INDENT]2a) Kill your X server control+alt+backspace. It will try to restart but will fail
2b)rename xorg.conf to something else
   ***sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.xgl***
2c)rename the backup back to xorg.conf 
   ***sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf***
2d)if you have a script file like /usr/bin/thefuture (may be a different name, edit it and comment out all lines by adding a # as the start of every line)[/INDENT]
3)start X, now without compiz/XGL.
  **startx**

This worked me on Dapper Drake 6.06 LTS

---

### Post by user1397 on 2006-10-22
> **nothingworks said:**
> I just removed compiz/XGL because my old pc was too sluggish with it.

Steps:
1) uninstall compiz and XGL using Symantic package manager (System->Administration)
2) Make sure you made a backup of your xorg.conf before installing XGL (below I assume it was xorg.conf.backup)[INDENT]2a) Kill your X server control+alt+backspace. It will try to restart but will fail
2b)rename xorg.conf to something else
   ***sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.xgl***
2c)rename the backup back to xorg.conf 
   ***sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf***
2d)if you have a script file like /usr/bin/thefuture (may be a different name, edit it and comment out all lines by adding a # as the start of every line)[/INDENT]3)start X, now without compiz/XGL.
  **startx**

This worked me on Dapper Drake 6.06 LTSthis is great to know.   however, i have since reinstalled ubuntu on my computer twice!  still though, if i ever need this again, thank you for posting it here.

---

