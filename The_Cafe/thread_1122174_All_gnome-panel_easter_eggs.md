---
title: "All gnome-panel easter eggs"
date: 2009-04-10
forum: The Cafe
---

### Post by Kenno on 2009-04-10
Let me first explain how this started. Surfing around, I stumbled upon a few cool Gnome Easter Eggs:
[LIST]
[*][GEGLs from outer space]("http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9131281&pageNumber=3") and
[*][free the fish]("http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9131281&pageNumber=2") (for an alternative way to unleash the fish, see [this blog post]("http://www.linuxtutorialblog.com/post/gnome-easter-egg-free-the-fish")).
[/LIST]
Problem is, there didn't seem any way to get rid of Wanda other than [restarting gnome-panel]("http://ubuntuforums.org/showthread.php?t=675111&p=4185631"), which I didn't want to risk at the point (even though it's fairly harmless). So I started digging through the gnome-panel source code. There doesn't seem any code in place to stop the fish from re-appearing, but when it goes off-screen, its graphics get unloaded from memory, so when it wants to come back, it has to reload them from disk. Knowing this, one can simply disable it with
```
cd /usr/share/gnome-panel/pixmaps
sudo mv wanda.png wanda.png.killed
```
and re-enable it with
```
cd /usr/share/gnome-panel/pixmaps
sudo mv wanda.png.killed wanda.png

```
Don't worry about making the panel crash by doing this; the code does check for the file's existence and simply goes back to "dormant state" if it doesn't find it.

Now comes the interesting part: figuring this out required digging through the gnome-panel "easter egg" code, which brought two more easter eggs to light:
[LIST]
[*]right-click on the panel, choose "properties", then right-click on the empty area at the right of the "Background" tab three times...
[*]whenever you get an error message (for instance, you can provoke one by pressing ALT-F2 and giving it a nonexistent application name such as "foo"), hold CTRL and type "FEAR". The box with the error message will become "afraid" of your mouse cursor. :lol:
[/LIST]

I haven't found these two easter eggs described on a website before, so they may be "novel". Happy easter. And next time a colleague leaves their console unlocked, you know what to do... :biggrin:

---

### Post by dragos240 on 2009-04-10
Hmm.... I can't get the fear one to work

---

### Post by tom66 on 2009-04-10
Me neither. Probably been removed.

---

### Post by Kareeser on 2009-04-10
Ha! I love Wanda the fish... if I could make it work through ssh and output on another display, there are a couple of poor saps who will wish they didn't give me an ssh login ;)

---

