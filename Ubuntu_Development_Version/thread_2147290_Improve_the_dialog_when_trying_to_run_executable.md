---
title: "Improve the dialog when trying to run executable"
date: 2013-05-21
forum: Ubuntu Development Version
---

### Post by ELD on 2013-05-21
This is something that has bugged me for some time, I am hoping someone can pick up on it and...in before someone tells me to do it myself I don't have the time.

When you try to run an application that you downloaded that hasn't been marked as executable the dialog box is not helpful at all, i see this type of post on my website all the time:
> I can't seem to run the executable. I unzip the files, then when I  double-click it, I just get told that there is no application  application installed for executable files.
Direct quote from a user!

Can this not be made more user friendly to _at least_ tell people how to do it if they wish to run it?

---

### Post by dino99 on 2013-05-21
Some times ago, when gtk2 was used, the user was having everything available from GUI; but devs was tired to get too much garbage reported by users tweaking all they was finding/reading from untrusted sources. So restrictions now exist with gtk3 and the latest ubuntu releases (less newbies errors)

---

### Post by Stinger on 2013-05-21
> I can't seem to run the executable. I unzip the files, then when I double-click it, I just get told that there is no application application installed for executable files.

Caja ( improved old Nautilus ) from [MATE]("http://www.linuxmint.com/rel_olivia_whatsnew.php#mate") can still do the trick :D

---

### Post by ELD on 2013-05-22
Is no one else bothered by this rubbish dialog?

---

### Post by dino99 on 2013-05-22
> **ELD said:**
> Is no one else bothered by this rubbish dialog?

If you are really concerned, then report against the appropriate package (zenity/dialog)

---

### Post by deri on 2013-05-22
I am tired of it. I have to everytime locate the package with dolphin.

---

### Post by dino99 on 2013-05-22
> **deri said:**
> I am tired of it. I have to everytime locate the package with dolphin.

nautilus have the "search" feature; but its not that thread purpose. ;) so open your own thread instead of hijacking here.

---

