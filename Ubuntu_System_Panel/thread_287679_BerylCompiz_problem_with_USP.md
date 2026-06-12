---
title: "Beryl/Compiz problem with USP"
date: 2006-10-29
forum: Ubuntu System Panel
---

### Post by plueken on 2006-10-29
This may be an old problem, and if so I apologize.  But I've often had a problem with USP conflicting with Beryl and, in the past, Compiz.  I have my USP panel in the bottom left of the screen, and it works fine until I either click, say, All Applications or click the panel to close it.  Then it moves itself some distance above the panel.

It's a minor problem, but it's really aesthetically annoying.  Since this forum is primarily USP users, and a constantly increasing number of Ubuntu users are switching over to using Beryl as well, I figured that if anybody had any experience with this bug, they would be here.  Any help is thoroughly appreciated in advance.

---

### Post by its_me_gb on 2006-10-29
Just moving the menu with beryl won't make it permenant. open gconf editor, and find the key
```
/apps/usp/panel_size
```

and set it to something like 1. i don't think 0 works though.

somebody correct me if im wrong.

---

### Post by Hanj on 2006-10-31
I have this same problem. I tried setting panel_size to 1, but that didn't do anything it seems.

---

### Post by metathran on 2006-10-31
Same for me since the first release of beryl, so i've switched to the SUSE gnome menu for ubuntu. I'm Waiting for usp2 to see how it works with beryl

---

### Post by nomeutente on 2006-11-01
Same problem for me

---

### Post by Malac on 2006-11-02
I've "upgrade" to beryl on edgy today and USP works fine for me.
My USP is on the bottom panel left hand corner. and my panel_size gconf is set to 24 same as my gnome panel size(right-click>properties).
[ATTACH]19217[/ATTACH]

---

### Post by Foxmike on 2006-11-05
Well, it seems to be a Beryl/Compiz problem, since I got this annoyance with both USP and gDesklets.  gDesklets wokrs well with Metacity as window manager, but if I have some desklets in the bottom part of the screen when changing to Beryl window manager, all those desklets are moving up a certain line, same as USP.

---

### Post by Malac on 2006-11-15
Just tried beryl again after an fglrx fiasco and now get this:
[ATTACH]19426[/ATTACH]
Hmmmm interesting. :-k

And no, it hasn't been flipped in image viewer. :-D
Left-to-Right seems okay but Up-to-Down seem to be switched.

---

