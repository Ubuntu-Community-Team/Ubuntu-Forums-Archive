---
title: "Screengrabs.. How do I..."
date: 2008-11-16
forum: The Cafe
---

### Post by Swagman on 2008-11-16
Take a screengrab from the dos prompt ?

I'm not talking about terminal /Konsole but ctrl + alt + F2 then login.
Yes I want to take a screeny of that text screen !!

If peeps press that combination and cant get back then press ctrl + alt + F7

Its bugging me thats all.

---

### Post by diablo75 on 2008-11-16
You should probably install Ubuntu inside Virtualbox and then take a screenshot.

---

### Post by Swagman on 2008-11-16
Two instances of ubuntu running ?

There must be an easier way .... One that doesn't involve a camera as well ?

---

### Post by voteforpedro36 on 2008-11-16
First, dos prompt? Lol, its a tty.

And second, search Synaptic. Maybe scrot can do it.

---

### Post by Swagman on 2008-11-16
Ta

Will do

+ Thanks

---

### Post by Phenax on 2008-11-16
fbgrab if you have a framebuffer on the tty

---

### Post by Swagman on 2008-11-16
Nah... Not working

I get Giblib error Cant open X server. It *is* running yeah ? Message.

Oh well.. I'll put that down to a phailZ on my part.

---

### Post by sirjoebob on 2008-11-16
Why dont you just run whatever it is in a terminal in the graphical view?

---

### Post by elmer_42 on 2008-11-16
He probably wants to take a picture of his text login. The only way I have [seen it done]("http://www.russ.co.il/images/fbshot.png") is with fbgrab.

---

### Post by Swagman on 2008-11-16
> **elmer_42 said:**
> He probably wants to take a picture of his text login. The only way I have [seen it done]("http://www.russ.co.il/images/fbshot.png") is with fbgrab.

Bingo

I installed fbgrab but it required the usual eleventy billion parameters that I can't be arsed to go lookup just to do something that's not really important.

+  thanks for the fbgrab recommendation anyway

---

### Post by FuturePilot on 2008-11-16
> **Swagman said:**
> Bingo

I installed fbgrab but it required the usual eleventy billion parameters that I can't be arsed to go lookup just to do something that's not really important.

+  thanks for the fbgrab recommendation anyway

To get a simple screenshot with fbgrab you really don't need to use any parameters.
```
fbgrab filename.png
```
should do the trick.

---

