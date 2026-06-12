---
title: "Move the menu?"
date: 2006-08-03
forum: Ubuntu System Panel
---

### Post by jISh on 2006-08-03
Mine's got a gap between my top gnome panel and the actual menu. How can I move it around?

---

### Post by _profox on 2006-08-03
Seems to be a metacity problem, again :) main development is done on Compiz window manager by chanders, so in the normal window manager (metacity) things don't always work like they should.. We will see what we can do though. (Please post bugs on our launchpad [http://www.launchpad.net/products/usp](http://www.launchpad.net/products/usp) btw)

---

### Post by jISh on 2006-08-03
Alright, I'll post it over there.
Seems to be another reason prodding at me to install Compiz...:O

---

### Post by chanders on 2006-08-03
> **jISh said:**
> Alright, I'll post it over there.
Seems to be another reason prodding at me to install Compiz...:O

There is a setting in /apps/usp/panel_size. By using values in there you can tweak USP to get it just the way you like ;-)

---

### Post by _profox on 2006-08-03
> **chanders said:**
> There is a setting in /apps/usp/panel_size. By using values in there you can tweak USP to get it just the way you like ;-)

Actually, on my metacity laptop that doesn't change -anything-

---

### Post by hanzomon4 on 2006-08-05
I got that gap and I'm running compiz

---

### Post by chanders on 2006-08-05
> **hanzomon4 said:**
> I got that gap and I'm running compiz

Try restarting the applet when you make the change...

---

### Post by hanzomon4 on 2006-08-06
Nope still got the gap
I set panel-size to 40, killall gnome-panel result.. usp is still the same size and the gap is still their

---

### Post by chanders on 2006-08-06
> **hanzomon4 said:**
> Nope still got the gap
I set panel-size to 40, killall gnome-panel result.. usp is still the same size and the gap is still their

OK I will look into it. Anyone had this problem and got it solved? I think hanzmon4 is using compiz..

---

### Post by hanzomon4 on 2006-08-06
Okay thanks, It's not to big of deal.
Everything else works great

---

### Post by stalefries on 2006-08-08
For those who just get bugged about it, you can fix it each time it happens by alt+dragging the window. 

In detail: Hold down alt, then click and drag any portion of the menu.

---

### Post by LordMau on 2006-08-09
> **hanzomon4 said:**
> Nope still got the gap
I set panel-size to 40, killall gnome-panel result.. usp is still the same size and the gap is still their

If panel-size is set to 1 what happens?

---

### Post by Uncle Spellbinder on 2006-08-09
> **LordMau said:**
> If panel-size is set to 1 what happens?

I just tried it. For me, nothing happens.

---

### Post by hanzomon4 on 2006-08-10
Could it be a schema problem?

---

### Post by hanzomon4 on 2006-08-13
The gap is gone with the latest usp and panel size set to 1

---

