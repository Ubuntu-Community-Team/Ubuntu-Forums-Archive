---
title: "Screen flashes black when opening Wine application"
date: 2009-05-31
forum: Wine
---

### Post by Colinho on 2009-05-31
Well that is pretty much it - every time I open an application in Wine, or do something in that application in Wine, the screen flashes black for a few seconds, and then goes back to normal. It's kind of like when you do an automatic screen adjustment.

I'm running 9.04 with Wine 1.1.22

---

### Post by nolliecrooked on 2009-05-31
> **Colinho said:**
> Well that is pretty much it - every time I open an application in Wine, or do something in that application in Wine, the screen flashes black for a few seconds, and then goes back to normal. It's kind of like when you do an automatic screen adjustment.
 
I'm running 9.04 with Wine 1.1.22
 
graphics card=?

---

### Post by hikaricore on 2009-05-31
Aside from giving us moer info as nollie suggested.. please try disabling desktop effects, running the application from a terminal window, and verifying that said application actually runs under WINE. (since you probably didn't read the sticky)

---

### Post by Colinho on 2009-05-31
My Graphics card is an ATI Radeon x1650.

Disabling desktop effects doesn't help.

The flashing is not a unique problem associated with a specific application, it's with all wine apps. To answer the question, yes these programs worked under 8.10, and the flashing happens even when I open the notepad that comes with wine.

How do I run a wine application in the terminal? Sorry, I'm not that experienced.

---

### Post by nolliecrooked on 2009-05-31
> **Colinho said:**
> My Graphics card is an ATI Radeon x1650.
 
Disabling desktop effects doesn't help.
 
The flashing is not a unique problem associated with a specific application, it's with all wine apps. To answer the question, yes these programs worked under 8.10, and the flashing happens even when I open the notepad that comes with wine.
 
How do I run a wine application in the terminal? Sorry, I'm not that experienced.
 
ok basically you have a choice, go back to 8.10 or Windows. ATi have dropped support for all cards before the HD2000 series, and the Linux drivers will only work with Ubuntu 8.10 or before. Im guessing your using the crappy opensource driver on Jaunty, or did you hack the 9.3 Catalyst somehow?

---

### Post by Colinho on 2009-05-31
Haha thanks. Well I guess I'll stick with 9.04 and then boot up into Windows on the odd occasion that I need to use a windows app.

Yep, I'm using the crappy opensource driver. Perhaps I'll look into getting a better graphics card.

---

### Post by nolliecrooked on 2009-05-31
> **Colinho said:**
> Haha thanks. Well I guess I'll stick with 9.04 and then boot up into Windows on the odd occasion that I need to use a windows app.
 
Yep, I'm using the crappy opensource driver. Perhaps I'll look into getting a better graphics card.
 
they have dropped support for Windows BTW :P, but yeah, any semi decent nVidia card (7300GT onwards) will do. the difference between the quality of nVidias drivers and ATis for Linux is pretty huge. go with nVidia!

---

### Post by Colinho on 2009-05-31
On Windows I mostly use Photoshop, and a few other small programs - nothing really that requires heavy use of a graphics card.

Is there a particular nVidia card that you recommend?

---

### Post by nolliecrooked on 2009-06-01
> **Colinho said:**
> On Windows I mostly use Photoshop, and a few other small programs - nothing really that requires heavy use of a graphics card.
 
Is there a particular nVidia card that you recommend?
 
if your only a light gamer (World of Warcraft etc...) then I would recommend a GeForce 9600GT if you have a PCI-E capable motherboard. if ya only have an AGP slot, then a 7300GT would be your best choice.
 
hope that helps (y)

---

### Post by Colinho on 2009-06-01
Cheers, thanks heaps!

---

