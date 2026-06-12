---
title: "[SOLVED] [Idea] Triage Mozilla bug 244787 and eventually add a window resize grip to"
date: 2007-10-18
forum: Ubuntu Brainstorm
---

### Post by amano on 2007-10-18
**Summary:**
Find the reason, why firefox doesn't show a resize grip in the bottom left corner and fix it.

**Scope and Use cases:**
Asa uses a theme with thin borders and has to fiddle any time if he wants to resize any Fx window.

**Rationale:**
Firefox is a pretty popular app on Ubuntu, probably the most popular app of them all. And this seems to be a big usability issue. ALL GNOME apps - at least the most popular ones - should have a resize grip for usability and coherence.

**Implementation Plan:**
1) Have asac read Mozilla  bug 244787: [https://bugzilla.mozilla.org/show_bug.cgi?id=244787](https://bugzilla.mozilla.org/show_bug.cgi?id=244787)
2) Triage the bug and find out if this is a Firefox bug, a GNOME bug, a distribution issue, or due to other reasons. The Firefox people seem to think that this is NOT a firefox bug.
3) Add this information to the firefox bug, file new bugs (GNOME, Ubuntu,...), or fix the bug by yourself.

---

### Post by Zdravko on 2007-10-18
This is a small bug. It does not deserve that big attention. There are many more other much more important bugs.

---

### Post by amano on 2007-10-18
If you don't resize firefox windows often or you don't use firefox at all, it might be a small bug for you. 

For me it is a big usability issue in the most used app (just guessing) of Ubuntu.

---

### Post by Zdravko on 2007-10-19
I use Firefox, but I never resize it. I use it maximized.

---

### Post by amano on 2007-10-20
It was announced that Firefox 3 will use a more native approach for windows, linux and so on. Thus it will have to be evaluated if maybe this move will fix the missing resize grip problem.

---

### Post by mech7 on 2007-10-20
Plz fix the backspace button too.. god i hate that bug :p I think i will never learn that it does not work under linux.

---

### Post by AusIV4 on 2007-10-20
> **mech7 said:**
> Plz fix the backspace button too.. god i hate that bug :p I think i will never learn that it does not work under linux.

Point your browser to 'about:config'. 
Search for the preference name "browser.backspace_action". 
Change the value from 1 to 0.

I do wish they'd do that in the release version, but it's easy enough to replace if you know what you're doing.

---

### Post by Zdravko on 2007-10-20
Yeah, that backspace bug is nasty.

---

### Post by mech7 on 2007-10-21
> **AusIV4 said:**
> Point your browser to 'about:config'. 
Search for the preference name "browser.backspace_action". 
Change the value from 1 to 0.

I do wish they'd do that in the release version, but it's easy enough to replace if you know what you're doing.

Ah thanks i didn't know i could fix it that easy :D

---

### Post by FrankQuist on 2007-10-21
Backspace thing is not a bug but a deliberate decision. See list: [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2007-October/thread.html#2099](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2007-October/thread.html#2099)

But that is off-topic and could be discussed elsewhere I guess.

Zdravko: Not everyone acts like you in their firefox behaviour.

---

### Post by 23meg on 2008-01-29
The bug is now fixed, and Firefox 3 in Hardy has the resize handle.

---

### Post by amano on 2008-01-29
Great to hear. Another very annoying issue went away. :guitar:

EDIT: Now I see that the corrispondent Mozilla Bug was marked verified fixed: [https://bugzilla.mozilla.org/show_bug.cgi?id=244787](https://bugzilla.mozilla.org/show_bug.cgi?id=244787)

Thus I could gladly remove my vote from the voting list ;)

---

### Post by Rufe0 on 2008-01-30
I dont have this bug but I do feel to multidirection resize box over corners is too small, you have to be like directly over the corner pixel, it should be like 25pixels atleast

---

### Post by amano on 2008-01-30
The bad thing is that still some default gnome apps lack the resize widget, especially MOST of the GNOME games (at least on gutsy): Blackjack, Five or More, glChess, Gnometris, Klotski, Mahjongg, Mines, Nibbles, Robots, Same GNOME, Tetravex and Four in a Row!

Reversi cannot be resized at all and Tali is at a fixed size!!

Just Sudoku und Aislerot do it right.

---

### Post by amano on 2008-01-30
The bad thing is that still some default gnome apps lack the resize widget, especially MOST of the GNOME games (at least on gnome 2.20.3): Blackjack, Five or More, glChess, Gnometris, Klotski, Mahjongg, Mines, Nibbles, Robots, Same GNOME, Tetravex and Four in a Row!

Reversi cannot be resized at all and Tali is at a fixed (unmaximised) size!!

Just Sudoku und Aislerot do it right.

Some related bugs: [http://bugzilla.gnome.org/show_bug.cgi?id=451906](http://bugzilla.gnome.org/show_bug.cgi?id=451906)

---

