---
title: "My waste basket's too big!"
date: 2009-05-29
forum: The Cafe
---

### Post by t0p on 2009-05-29
Okay, I know this isn't the place to post bug reports.  But I'm hardly gonna to that about this *now* - I've been using Hardy for a year, I noticed this "bug" the first day, and I don't really care.  Well, clearly I *do* care, otherwise I wouldn't be typing[*] this, would I?

Anyway...  when the waste basket at the bottom right of the screen (in Hardy) has garbage in it, it's the correct size.  But when it's empty, it's *huge*!  I won't say *too* huge, because any sized empty waste basket is too big.  But still, it ain't right.

[*] Yeah, I typed "typing".  I didn't keyboard "keyboarding" because that use of keyboard really grrinds me down.  I know the use of "type" in this context is anachronistic, but I don't care!  After all, the TARDIS is anachronistic but the Doctor still uses it.  And what's good enough for the Doctor is good enough for me!  :p

---

### Post by fatality_uk on 2009-05-29
ScreenShot would be helpful.
One mans huge is another mans average!

---

### Post by bryonak on 2009-05-29
When it's empty, try right clicking on it and select "Restore icons original size". If that's greyed out, select "Stretch icon" and make it smaller. Maybe it will keep the size for that particular icon.

---

### Post by t0p on 2009-05-30
**fatality_uk**, I have attached screenshots for you to peruse.  (Sorry for the messy Desktop.)  Enjoy!

**bryonak**, when I right-click on the basket I don't get the options you referred to.  All I get is: Open, Empty the Deleted Items Folder, Help, About, Remove from Panel, Move, Lock to Panel.  :(

---

### Post by spcwingo on 2009-05-30
I have no idea what the problem is, but I'm also running Hardy...no problems here.  :-k

---

### Post by ssam on 2009-05-30
try choosing a different theme.

it is possible that your theme is not loading properly (unless you have chosen the minimal one you have now). if you run
```
gnome-settings-daemon
```
in a terminal does the theme change?

---

### Post by t0p on 2009-05-31
> **ssam said:**
> try choosing a different theme.

it is possible that your theme is not loading properly (unless you have chosen the minimal one you have now). if you run
```
gnome-settings-daemon
```
in a terminal does the theme change?

No.

```
t0p@ubunty:~$ gnome-settings-daemon

** (gnome-settings-daemon:19160): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:19160): WARNING **: Could not acquire name

```

Is this bad?  (I've got this phobia about when my computer says WARNING ** at me).  :(

---

### Post by t0p on 2009-05-31
Well, I changed my theme (pleasant but boring blubuntu) and the trash can is now "normal".

But the **gnome-settings-daemon** still gives that ominous WARNING ** warning.  I'm scared...

---

### Post by Rotarychainsaw on 2009-05-31
Yeah, it's just the icon theme you chose. The author probably didn't include the correct size for the empty icon. Ask the author to make one or find another theme.

---

### Post by HappyFeet on 2009-05-31
Nice wallpaper tOp. ;)

---

