---
title: "Virtualbox fullscreen problem"
date: 2008-04-09
forum: Virtualisation
---

### Post by pedrobl on 2008-04-09
I know this subject has been showing up in the forums, but I couldn't find a similar case.

I'm using ubuntu 7.10 (fully updated, no compiz), and I've installed devilspie to fullscreen my xp virtualbox machine. 

The first time I run it, I get perfect fullscreen with no panels, but as I hit right-ctrl-f to leave the full screen mode to move to another desktop, i get a window with a 1024x768 content that I cannot fully see (i have a 1024x768 monitor). If I try Rctrl-f again, I get a desktop with top and bottom pannels, a black border, and a piece of the windows screen, still in 1024x768... any ideas how i could get rid of the gnome panels?

I enclose an image of the desktop.

TIA,

Pedro.

---

### Post by pedrobl on 2008-04-09
If I enable auto resize, I can make it to work. The problem is that every time I leave full screen mode, the guest window resolution changes, and I don't think windows likes too many resolution changes.

I've search the virtualbox.org site, and I found a bug filed 4 months ago: [http://www.virtualbox.org/ticket/972](http://www.virtualbox.org/ticket/972), but it hasn't been assigned yet.

Cheers,

Pedro.

---

### Post by jbaerbock on 2008-04-09
I'm running Ubuntu 7.10 in virtualbox on WindowsXP. I can do ctrl+F to go to fullscreen but OS doesnt change size. I would like to be able to make ubuntu running in VB fullscreen in windows if possible. Any ideas?

---

### Post by Windreaver on 2008-05-05
Got the same issue.  I'm running main OS Ubuntu 8.04 with VirtualBox carrying Windows XP.  I put full screen on but a black boarder just appears around the box and the simulation stays the original size of the virtual window. 

Anyone?  


Ill mess around with it more and see what I can find out.  :)


*EDIT*
Ok so inside the WinXP in VBox I changed the windows resolution to 1280x1024 then hit Ctrl+f to go full screen and it filled my monitor perfectly. My main OS Ubuntu screen res is set at 1024x768.

So if you're running Win xp in VirtualBox - this will make you happy.\\:D/

Pretty easy fix.

---

### Post by NOLU on 2008-05-10
Probably something really basic but when I change my screen res, there are only two option and the highest 1024x768

I've still got a border when I go full screen so is there a way of getting rid of the border or upping my resolution?

---

### Post by MyR on 2008-05-28
> **NOLU said:**
> I've still got a border when I go full screen so is there a way of getting rid of the border or upping my resolution?

I had this problem and solved it by increasing the guest video memory to 10MB.  Now the guest resolution automatically changes when I go to fullscreen and changes back when I exit fullscreen.

peace

---

### Post by NOLU on 2008-05-28
I followed this guide in the end and found out I wasn't using 'seamless mode'.

All working well now except for if I click on anything like the start menu, the XP desktop disappears and the Ubuntu one shows up but I can still run things like Winamp :D

[http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux](http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux)

---

### Post by MyR on 2008-05-28
> **NOLU said:**
> All working well now except for if I click on anything like the start menu, the XP desktop disappears and the Ubuntu one shows up but I can still run things like Winamp :D

I would guess that if you disable compiz (set visual effects to none) it will solve this problem.

hope this helps!

peace

---

### Post by Gaud3t3 on 2008-09-10
Thanks everyone!! much love for all the help!!!:popcorn:

---

### Post by bvanevery on 2009-03-05
For anyone hosting an Ubuntu guest in Windows XP, I found this URL to be a big help with the resolution problem: 

[http://tombuntu.com/index.php/2008/05/23/install-virtualbox-additions-for-an-ubuntu-804-guest/](http://tombuntu.com/index.php/2008/05/23/install-virtualbox-additions-for-an-ubuntu-804-guest/)

In my case, the guest additions for Ubuntu contained the necessary updates for displaying at a higher resolution.

---

