---
title: "What does this Wine Error Code mean?"
date: 2011-01-13
forum: Wine
---

### Post by Dangerzone812 on 2011-01-13
I was playing Mass Effect one through PlayOnLinux, with the mouse patch installed, and it was working well during the opening menus making a new character, but just as I was about to start a new game, it just hit a black screen, played some music, then stopped and this error popped up, what does it mean?! 

Thanks in advance,
Danger.

---

### Post by cogadh on 2011-01-14
It doesn't mean much. That's a general protection fault, any number of things can cause that. The fact that the particular error you got produces a whole ton of "filename not found" messages makes it virtually impossible to track down where the actual error is occurring. That being said, odds are you are running into this known problem with ME on Wine:
[http://bugs.winehq.org/show_bug.cgi?id=25127](http://bugs.winehq.org/show_bug.cgi?id=25127)

---

### Post by Dangerzone812 on 2011-01-14
Well I think I just need Patch 1.02, but I don't know where to find that, or how to install it, I'm so new to this all, I need someone to explain it to me how to install it from A-Z, as if to a 5 year old child, because thats about my level of understanding of Linux. Lol

---

### Post by cogadh on 2011-01-14
If you are talking about the 1.02 patch for the game, you can probably find that on the game's website, if the game itself doesn't include some kind of built-in update utility. As for applying the patch, it is no different on Linux than it is on Windows; simply double-click the file you download and it should launch with Wine.

BTW - Honestly, I wouldn't expect ME to work all that well in Wine if I were you. The game doesn't get higher than a "silver" rating on Wine's Application Database and it does not even get that consistently (it gets more "bronze" and "garbage" ratings than anything else). Generally speaking, unless an app consistently gets "silver" or higher ratings, its probably not worth bothering with yet.

---

### Post by Dangerzone812 on 2011-01-14
I honestly like Linux, but the fact that I can't play games is a killer.

---

### Post by cogadh on 2011-01-14
If you want to play Windows games, you are usually better off just staying with Windows. Wine is great for games that are from the DirectX 9 or older era, but most games from the DirectX 10 and newer era aren't going to work that well (yet).  

However if you just want to play games regardless of the OS, then you might want to check out some of the Linux native games that are available. They aren't all bad solitaire clones and some of the AAA titles you can find on Windows actually do have Linux ports.

---

