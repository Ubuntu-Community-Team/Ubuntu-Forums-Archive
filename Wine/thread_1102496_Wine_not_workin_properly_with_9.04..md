---
title: "Wine not workin properly with 9.04."
date: 2009-03-21
forum: Wine
---

### Post by armen87 on 2009-03-21
Hi, I have upgraded to ubuntu 9.04, everything ok but wine does not work properly, I use it to play spider solitaire but know I cant. Black spots appear when moving cards from one place to another. I tried redownloading the .exe file but the problem persists.
[IMG]http://img21.imageshack.us/img21/2981/pantallazo1j.png[/IMG]

---

### Post by Kosimo on 2009-03-21
> **armen87 said:**
> Hi, I have upgraded to ubuntu 9.04, everything ok but wine does not work properly, I use it to play spider solitaire but know I cant. Black spots appear when moving cards from one place to another. I tried redownloading the .exe file but the problem persists.
[IMG]http://img21.imageshack.us/img21/2981/pantallazo1j.png[/IMG]

Which videocard are you currently using? (Drivers?)

How did you install wine?

---

### Post by armen87 on 2009-03-21
ati radeon 9250, I didnt add any drivers, when I installed ubuntu 8.10 I had the graphics acceleration already working. I had wine stable version from ubuntus add/remove programs and the thing worked well but after upgrading to 9.04 this black things appear. I just tried downloading the latest version of wine 1.1.17 but it doesnt solve the problem.

---

### Post by Kosimo on 2009-03-21
> **armen87 said:**
> ati radeon 9250, I didnt add any drivers, when I installed ubuntu 8.10 I had the graphics acceleration already working. I had wine stable version from ubuntus add/remove programs and the thing worked well but after upgrading to 9.04 this black things appear. I just tried downloading the latest version of wine 1.1.17 but it doesnt solve the problem.

OK then you're using MESA drivers.
Let's try to give WINE a virtual desktop

GO to Applications - Wine - Configure wine

Graphics tab and then select "Emulate a virtual desktop" 
choose 800x600, hit apply and try again.

---

### Post by ajgreeny on 2009-03-21
> OK then you're using MESA drivers.
Let's try to give WINE a virtual desktop

I think you will find that the ati 9250 works well with the open source radeon driver which will have been installed and used from the time you installed the system.

But why do you need to use wine to play spider solitaire?  Go to **Menu > Games > AisleRiot Solitaire > Select Game** and you can choose spider and many many others as well.  There's no need to bother with wine.  Perhaps that game is not yet with jaunty, but if not, I'll bet it will be when it eventually appears in final form.

---

### Post by Kosimo on 2009-03-21
> **ajgreeny said:**
> I think you will find that the ati 9250 works well with the open source radeon driver which will have been installed and used from the time you installed the system.

But why do you need to use wine to play spider solitaire?  Go to **Menu > Games > AisleRiot Solitaire > Select Game** and you can choose spider and many many others as well.  There's no need to bother with wine.  Perhaps that game is not yet with jaunty, but if not, I'll bet it will be when it eventually appears in final form.

That's a much much better solution :)
Always better using native apps.

---

### Post by armen87 on 2009-03-21
I think the same... but the problem is that I am not the one playing spider. My mom is the one who plays it, she tried native spider games but she doesnt like them.....:(

---

### Post by armen87 on 2009-03-21
I have tried "Emulate a virtual desktop" but it doesnt solve the problem... I will wait untill jaunty is stable... If you got another suggestion I will try it...

---

### Post by t3ch on 2009-03-22
Helo!

I have installed 9.04 and wine isn't working properly with worms mayhem too!
I have played it on 8.04 and 8.10 and it work greate with patched dinput.dll.so if u placed it to /usr/lib/wine ..

Now is the problem when you centering some worm mouse start bumping up and down..

but iam using ext4 and iam happy that it works =)

about bumping of mouse in wine.. have anyone some fix for that? 

tnx in advance:KS

---

