---
title: "EasyLin. What do you think about this project ?"
date: 2008-08-10
forum: The Cafe
---

### Post by michu2510 on 2008-08-10
Hello, EasyLin it's a program to easy install hardware. For example: to install you printer you must write 30 lines in console, but now it's EasyLin withe this program you can install it withe 4 clicks. Now it's working withe about 100 hardwars. If you can't install your hardware please contact via mail: [email]easylin.pl@gmail.com[/email] or to me via jabber:michu2510@jabster.pl . If you got any suggestions please write it in this topic.For programmer : we are looking for help in creating this project, we need: webmasters, bash,python, or another language programmer, testers.

---

### Post by miggols99 on 2008-08-10
Yes...you have to write 30 lines in the terminal...even with Arch Linux I don't have to do that much! With Ubuntu it's automatic (with open source drivers anyway). So it's pretty pointless to make a program to do this. Maybe you should join an existing project...

---

### Post by bobbocanfly on 2008-08-10
> **michu2510 said:**
> to install you printer you must write 30 lines in console

Hmmm...I seemed to plug mine in and it worked when I hit print. I'd like to see a printer that takes that much effort to setup.

---

### Post by BigSilly on 2008-08-10
30 lines of code??!

I plugged mine in and it installed itself almost instantly. Sounds like someone's idea of a joke...

EDIT: Careful what name you choose btw. [Someone already owns the name easyLIN...]("http://www.micronas.com/automotive_and_industrial_products/by_function/easyLIN/index.html")

---

### Post by Canis familiaris on 2008-08-10
> **BigSilly said:**
> 30 lines of code??!

I plugged mine in and it installed itself almost instantly.
+1

Maybe he is talking of Lexmark's Printers?

---

### Post by Mr. Picklesworth on 2008-08-10
I think you may find better success looking for the project that deals with printer autodetection in Launchpad and working on a branch for that, rather than launching another new oddball project. For one thing, that would be better for users who want their printers to just work without installing some weird script. It means less work for you since most of the project already exists. Finally, this means that if your patch is indeed effective it would find its way to default Ubuntu and back upstream quite quickly.

Generally speaking, though, I think the problem is lack of drivers more than anything. Perhaps look into packaging printer drivers and contributing those, or working on an infrastructure to auto install printer drivers via apt (so that more can be available, just the less common ones not on local disk), since the actual detection is generally quite solid.

---

### Post by ghindo on 2008-08-10
> **michu2510 said:**
> Now it's working withe about 100 hardwars.lol

---

### Post by michu2510 on 2008-08-11
This 30 lines in console it was example, my hp is running whiteout installing anything. But to install Brother you must do many things. I know 100 hardwares it's funny but it is new project.

---

### Post by Lexicon101 on 2008-08-11
wars are hard for anyone.. just try to work through it.

---

### Post by VitaLiNux on 2008-08-11
> **Mr. Picklesworth said:**
> I think you may find better success looking for the project that deals with printer autodetection in Launchpad and working on a branch for that, rather than launching another new oddball project. For one thing, that would be better for users who want their printers to just work without installing some weird script. It means less work for you since most of the project already exists. Finally, this means that if your patch is indeed effective it would find its way to default Ubuntu and back upstream quite quickly.

Generally speaking, though, I think the problem is lack of drivers more than anything. Perhaps look into packaging printer drivers and contributing those, or working on an infrastructure to auto install printer drivers via apt (so that more can be available, just the less common ones not on local disk), since the actual detection is generally quite solid.

Kudos to you, Mr. Picklesworth:guitar:

---

