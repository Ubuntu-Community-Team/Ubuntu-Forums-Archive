---
title: "WC3 The Frozen Throne Running problems"
date: 2009-01-14
forum: Wine
---

### Post by mfr1003 on 2009-01-14
Heya folks.  Just having trouble running the Fronzen Throne.  Got both ROC and TFT installed fine.  ROC works just grand.  When I try to start TFT, I get a black screen that never loads to the menu.  I know that the Cinematics of these two games are raising all kinds of hell with linux.  Fine, I don't care about the cinematics.  I know most of you have probably seen all the cinis at least 5 times like I have.  ;)

The clincher is I had this problem with ROC in the beginning as well.  If memory serves, all I did was ask PlayonLinux (I use WINE and not cedega) to use an older version of WINE instead of the one my OS has loaded and running.  Does TFT not work on WINE 0.9.58?  Do I have to run ROC with 9-58 and TFT with the system's default?  who do I have to strangle to find out the creator of this back-a$$wards logic?

So basically, when I run TFT, I get a black screen, and two things running: Blizzard Player, which I'm assuming is the cini, and what I can only assume is War3.exe.  Can I just change it to not attempt to play the cini, is that possible?

Signed,

-Desperate

---

### Post by MindFlayer on 2009-01-14
Don't worry, those cinematics raise a lot of problems on Windows platforms as well. :)

I think you could try to disable the first intro by running "wine regedit" and then modifying the following registry variable:
HKEY_CURRENT_USER/Software/Blizzard Entertainment/Warcraft III/Misc/seenintromovie

Set its value to "1" and see if it helps.

---

### Post by mfr1003 on 2009-01-14
Hey, I made it to the Reg.  There is no Misc.

[[IMG]http://img398.imageshack.us/img398/7733/scrn1regeditor1.th.jpg[/IMG]](http://img398.imageshack.us/my.php?image=scrn1regeditor1.jpg)

What now?

---

### Post by MindFlayer on 2009-01-14
Hmm, that looks different to mine.

[[IMG]http://img108.imageshack.us/img108/4382/regedyu6.th.png[/IMG]](http://img108.imageshack.us/my.php?image=regedyu6.png)

Try to create the "Misc" key by hand and insert the seenintromovie in it as a DWORD value.

One more thing worth trying would be to start the game with the parameter -window and see if the cinematics work then.

---

### Post by hotweiss on 2009-01-14
FT runs perfectly on Wine 1.1.12

---

### Post by binbash on 2009-01-14
did you try to rename movie folder?

---

### Post by mfr1003 on 2009-01-14
Hey folks.  thanks for your help.  previous issue is solved tft is working on 0.9.58 PoL.  Now, next question is Hosting.  any ideas?  No one can join my games.  is this a common issue?

---

