---
title: "No menus in Libreoffice?"
date: 2012-09-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by sgage on 2012-09-03
I just installed from today's (4th!) build. All is well, except Libreoffice, at least Writer, has no menus! Anyone else have this issue?

---

### Post by pnarciso on 2012-09-03
I can confirm that using Xubuntu, latest update broke the menus.

---

### Post by sgage on 2012-09-03
> **pnarciso said:**
> I can confirm that using Xubuntu, latest update broke the menus.

I should have mentioned that I'm running Gnome Shell.

I checked in Unity, and the global menus up in the top panel were working.

---

### Post by mc4man on 2012-09-03
The one way I've found in Gs to get any sort of menus is to remove 
libreoffice-gtk
Otherwise you'll need to wait till somebody fixes something sometime down the road

---

### Post by Bowmore on 2012-09-03
Yep it's a regression, and here's the bug on that issue:
[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1044657](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1044657)

Probably a spinoff effect when solving this issue:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1041354](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1041354)

---

### Post by sgage on 2012-09-03
> **mc4man said:**
> The one way I've found in Gs to get any sort of menus is to remove 
libreoffice-gtk
Otherwise you'll need to wait till somebody fixes something sometime down the road

Thanks for the tip!

---

### Post by sgage on 2012-09-03
> **Bowmore said:**
> Yep it's a regression, and here's the bug on that issue:
[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1044657](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1044657)

Probably a spinoff effect when solving this issue:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1041354](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1041354)

Thanks for the pointers...

---

### Post by Yahoé on 2012-09-13
> **sgage said:**
> I should have mentioned that I'm running Gnome Shell.

I checked in Unity, and the global menus up in the top panel were working.

It definitely also affects Unity. A more specific bug report exists [1045906]("https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1045906")

---

### Post by Harry33 on 2012-09-13
A new version of the rc2 is building in Launchpad now, soon in repos:
libreoffice (1:3.6.1~rc2-1ubuntu4)
However, this is only for libpoppler27=>libpoppler28 transition (pdf-import)
and does not solve the menu issue.

---

### Post by dino99 on 2012-09-13
Libreoffice in Lubuntu Quantal have its menus :P

---

### Post by Harry33 on 2012-09-13
> **dino99 said:**
> Libreoffice in Lubuntu Quantal have its menus :P

So the QQ Libreoffice version rc2 does work in Lubuntu then?

---

### Post by dino99 on 2012-09-13
> **Harry33 said:**
> So the QQ Libreoffice version rc2 does work in Lubuntu then?

i dont think its related to that new rc as i've switched to Lubuntu Quantal (as gnome-classic) the first day i got libreoffice menu trouble on ubuntu quantal (need to use it daily)

---

### Post by jerrylamos on 2012-09-13
Zoom > Optimal is my choice for Open Office Writer, Libre Office Writer.

Hwo can I do that with QQ's Libre Office Writer?  Am I missing something?

Thanks for hints. 

Jerry

BTW, I can read text fine.  Little pictures don't mean much.  Does QQ have a dictionary with all the little pictures and what they mean?  "Mouse over" is very slow oing all across the various lines.  The Phoenicians had it all over Egyptian Hieroglyphics, my opinion.

---

### Post by Harry33 on 2012-09-15
This menu issue is fixed now.
There is a new Libreoffice build in QQ repos:
libreoffice (1:3.6.1~rc2-1ubuntu5)

Here:
[https://launchpad.net/ubuntu/quantal/+source/libreoffice/1:3.6.1~rc2-1ubuntu5](https://launchpad.net/ubuntu/quantal/+source/libreoffice/1:3.6.1~rc2-1ubuntu5)

---

