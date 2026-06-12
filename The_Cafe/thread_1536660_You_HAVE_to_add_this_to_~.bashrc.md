---
title: "You HAVE to add this to ~/.bashrc"
date: 2010-07-22
forum: The Cafe
---

### Post by AlphaLexman on 2010-07-22
I remember in college, the terminals did this, I didn't know how or why, but since I started with Linux, Ubuntu and bash, I hadn't found or figured it out. Until now.
```
# Use up and down arrow to search the history. Invaluable!
bind '"\e[A"':history-search-backward
bind '"\e[B"':history-search-forward
```# Thanks to Colin Barschel at [http://cb.vu/](http://cb.vu/)

---

### Post by RiceMonster on 2010-07-22
Isn't that the default behavior?

---

### Post by CharlesA on 2010-07-22
It does that already.

---

### Post by Joeb454 on 2010-07-22
I tend to edit /etc/inputrc to make PgUp / PgDn search history, I prefer it like that

---

### Post by Bachstelze on 2010-07-22
Escape-j/k is how I roll.

---

### Post by anon.jdh on 2010-07-22
"Linux's BASH shell keeps track of recently issued commands. This list is called the history list, and you can scroll back through it using the Up arrow key, or back down using the Down arrow key, just as you would with the Back and Forward buttons on a web browser."

from [http://oreilly.com/catalog/debian/chapter/book/ch04_01.html](http://oreilly.com/catalog/debian/chapter/book/ch04_01.html)

---

### Post by FuturePilot on 2010-07-22
Ctrl+R

You'll never search the same again.

---

### Post by Bachstelze on 2010-07-22
> **FuturePilot said:**
> Ctrl+R

You'll never search the same again.

Surely you meant Escape-/. ;)

---

### Post by AlphaLexman on 2010-07-22
I agree with Joeb454, the /etc/inputrc would be a much better place for my code.
I am not scrolling my history I am _searching_ it. (better than Ctrl-R) imo.

---

### Post by CharlesA on 2010-07-22
> **FuturePilot said:**
> Ctrl+R

You'll never search the same again.

That's quite handy!

---

### Post by anon.jdh on 2010-07-22
how's about this one:

My last command #66 was history but I don't want to type #64 again so...

if my history looks like this -->

   64  ps -aef | grep vnc | awk '{print$2}'
   65  clear
   66  history

I just type:

```
!64
```

skel@skeleton:~$ !64
ps -aef | grep vnc | awk '{print$2}'
1565
1569
1856
1860
2861


This saved me a whole 2 up arrows. But if you are going to repeat a long stringy command over and over, this is great.

---

### Post by AlphaLexman on 2010-07-22
Look, I can't explain what it does, or how it is better, in a forum, just try it. Type in the beginning of a history command (3-4 characters) and press the the up arrow key, multiple times if needed.

---

### Post by anon.jdh on 2010-07-22
Forums have a way of obfuscating actual, sincere tips.
There are lots of cool ideas in this thread that do different things. 

I think it's tight that there's so much flexibility, that's all.
Not being a smart-a** (for once).

---

### Post by sisco311 on 2010-07-22
> **Joeb454 said:**
> I tend to edit /etc/inputrc to make PgUp / PgDn search history, I prefer it like that

Yep, admins tend to edit whatever they can, I would add it to ~/.inputrc. :evil:

---

### Post by AlphaLexman on 2010-07-22
Thank you sisco311, I like your personal preference solution better!
FYI, Your posts/advice always informs me about new things!

---

