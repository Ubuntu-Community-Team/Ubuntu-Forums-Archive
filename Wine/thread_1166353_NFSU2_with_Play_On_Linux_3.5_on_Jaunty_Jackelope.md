---
title: "NFSU2 with Play On Linux 3.5 on Jaunty Jackelope"
date: 2009-05-21
forum: Wine
---

### Post by b@sh_n3rd on 2009-05-21
Hi, I'd like to know if it's possible to install and run Need For Speed Underground 2 on POL 3.5 which I've installed on Jaunty...I checked the list of apps on POL itself and though it mentions NFSU, (Underground 1), It doesn't say anything about NFSU2..Any help pls? Thanks for any help..

---

### Post by cogadh on 2009-05-21
POL is just a font end for Wine, so if you want to know if a particular game will work with it, you should check Wine's Application Database:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2846](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2846)

---

### Post by b@sh_n3rd on 2009-05-22
Well, I did check on it a couple of weeks ago...apparently in *might* run...but how do I install it on POL? I need a script or something right?

---

### Post by cogadh on 2009-05-22
Nope, you don't really need a script or POL to install it, just run the install in Wine like you would in Windows. Like I said, POL is just a front end for Wine, so that is really all it is doing with its scripts. If you really want to use POL, writing a script for it is not all that hard and they do have instructions on their website.

However, you might not want to waste your time with this particular game. According to the AppDB page for it, it doesn't get higher than a Bronze rating, which is not functional enough to really be playable. A silver rating is the bare minimum that you want to try and play a game with Wine, gold or platinum ratings are preferred.

---

### Post by b@sh_n3rd on 2009-05-22
Oh? coo...thanks for the tip...I found out that you could install by choosing the "autorun" command in POL itself. Anyways, I installed NFSU2 using wine and it RAN...the thing is, graphics was hopeless :( couldn't see a thing...all grey! why is this?

---

### Post by cogadh on 2009-05-22
Like I said, the game doesn't run fully in Wine yet. Chances are, it is trying to do something that Wine hasn't implemented, like some advanced graphics function.

---

### Post by Kareeser on 2009-05-22
Yep. A lot of users also find that their keyboard stops working in-game for whatever reason.

I gave up.

---

### Post by b@sh_n3rd on 2009-05-23
oh..ok...it's ok then...POL doesn't really DO anything with the game right? It just helps to install the game?

oh yeah, I *was* wondering why my keyboard functions didn't work :D..

---

### Post by cogadh on 2009-05-23
POL doesn't do anything that Wine can't already do on its own. Its really just an easier to use front end for people who don't necessarily like working with Wine in the terminal, though with the way Wine is there days, you really don't need the terminal too much.

---

### Post by b@sh_n3rd on 2009-05-23
Yeah, I just figured it out..POL is just advantageous to *Install* games isn't it? Quite easy...and just a few other options I noticed like simulating a "windows reboot"...

---

### Post by cogadh on 2009-05-23
For installing games, it does take some of the odd quirks of using Wine out of the process, but like I said, POL does not do anything that you can't already do with Wine. For example, you can simulate a reboot within Wine without POL, just open a terminal and type "wineboot".

---

