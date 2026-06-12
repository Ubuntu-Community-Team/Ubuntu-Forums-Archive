---
title: "HOWTO: Equations in Office 2007 (or others?)"
date: 2009-02-04
forum: Wine
---

### Post by NightMKoder on 2009-02-04
I just posted this on wine bugzilla: [http://bugs.winehq.org/show_bug.cgi?id=5264#c23](http://bugs.winehq.org/show_bug.cgi?id=5264#c23) .

Turns out all you have to do to get equations to work, (mostly), is set usp10.dll to native. EDIT: set riched20.dll to native to allow _/^ to convert properly. Otherwise they just stay like that instead of doing subscript/superscript.

For those of you who don't know how: just open wine config (Alt+F2->type winecfg), go to the libraries tab and type usp10.dll and click add.

The only thing that doesn't work is the menu of equation symbols (it just doesn't recognize the click...). Use the \whatever shorthands (\lambda, \lfloor, \rfloor). EDIT 3: You can just click the down arrow and expand the list. This will make the buttons clickable. (Thanks, rasmus) EDIT 2: Apparently it IS possible to click on them, you just have to click on the very corner. Don't let the zoom-in feature work, just go between two buttons and move slightly towards the one you need. It will highlight slightly and you can press it.

Tested on wine 1.1.14 (get from the wine website), Kubuntu Intrepid. 

Enjoy!

---

### Post by bramming on 2009-02-18
I love you man ! :)

I am currently working on a mathproject with my group and we just got screwed because they use office 2007 and i use openoffice.org. I have ms office installed but since equations didnt work we were screwed as said earlier. This fixed the prob ty

---

### Post by rasmus_ on 2009-02-25
Thanks for the info man, saved my day!

Also, there is no need to just go between two buttons and move slightly towards the one you need. Just press the Down Arrow on the right hand side in order to expand the list. There you can press the buttons normally. :p

---

### Post by eddyojb on 2010-11-27
thankyou!

---

### Post by hojjat on 2011-02-10
Save my day! Thanks.

---

### Post by ChrisEiffel on 2011-09-08
Thanks awesome fix

---

### Post by Thuener on 2011-09-21
Omg, that save my day!!

---

### Post by Mr.Pytagoras on 2012-01-07
Thanks, I was having similar problem however it wasn't rendering but crashing, the word 2007 crash when I tried to open a document which contained  equations, also it crashed if I added the equation in already opened doc, but this little howto fixed it :)

Thanks man

Edit:
using 
wine-1.3.15
ubuntu 11.04

---

