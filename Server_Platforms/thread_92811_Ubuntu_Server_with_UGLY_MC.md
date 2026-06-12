---
title: "Ubuntu Server with *UGLY* MC"
date: 2005-11-20
forum: Server Platforms
---

### Post by HunterCo on 2005-11-20
I love the Midnight Commander program... and I'll admit, I'm 100 times slower on the CLI without it. So imagine my dismay when I installed it onto a recent server installation only to find that I can barely make out what's going on. The screen is tweaked, and for lack of a better explanation, it looks like the terminal isn't displaying ANSI or ASCII characters (non-alphanumeric, that is).

MC works great on normal Ubuntu, so could someone help me figure out what I need to install to make it look right? Is it something along the lines of unicode? Is it a font issue? Maybe an ncurses thing? :confused: 

Thanks in advance.

-- HunterCo --
--------------
Please help me, Obi-wan Kenobi. You're my only hope!

---

### Post by darkfame on 2005-11-20
It's a charset problem, I had the same problem with mc.
I think dpkg-reconfigure console-data and dpkg-reconfigure locales will solve your problem.

---

### Post by petterah on 2005-11-20
Hi all, dpkg-reconfigure locales will fix this problem, select your locale from the menu, multible locales are allowed

---

### Post by HunterCo on 2005-11-21
I tried both of these...

sudo dpkg-reconfigure console-data
sudo dpkg-reconfigure locales

But MC still will only display alpha-numeric characters, and nothing along the lines of... lines. Now MC looks great when running in a terminal from XFCE, but from the CLI it's still terrible. I tried both the en_us choices, UTF-8 and the other standard, with no luck. I did notice a line on bootup:

Setting up general console font...          [OK]

Is there a place I can change this? I'm wondering if maybe this is the problem?

---

### Post by ranf on 2005-11-22
[QUOTE=HunterCo]
But MC still will only display alpha-numeric characters, and nothing along the lines of... lines. Now MC looks great when running in a terminal from XFCE, but from the CLI it's still terrible. I tried both the en_us choices, UTF-8 and the other standard, with no luck. I did notice a line on bootup:
[/QUOTE]
Try this thread. It helped me.
[http://ubuntuforums.org/showthread.php?t=75568&highlight=mc](http://ubuntuforums.org/showthread.php?t=75568&highlight=mc)

---

### Post by HunterCo on 2005-11-22
[QUOTE=ranf]Try this thread. It helped me.
[http://ubuntuforums.org/showthread.php?t=75568&highlight=mc](http://ubuntuforums.org/showthread.php?t=75568&highlight=mc)[/QUOTE]
Oh, great link. Thanks.
I thought I had done a search on this one, but I didn't see this thread before. I'll give it a shot (tried the first two, but never did change the font in the last step) and if I don't say anything more, it can be assumed it's fixed and working.

Thanks again, all, for the input and suggestions.

** UPDATE **
It works! Woohoo! It was a matter of changing that font name in /etc/console-tools/config after I re-ran the dpkg-reconfigure locales. You're all a bunch o' studs!

---

