---
title: "Libre office writer doesn't appear in launcher when active"
date: 2012-09-24
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ubername on 2012-09-24
Hi
When I have a libreoffice writer document open the icon does not appear in the launcher, nor does it appear in the 'alt tab' switcher list. Anyone else have this / know a solution? (Calc works fine FYI)

---

### Post by over_my_head on 2012-10-01
i seem to be having the same problem. 
if i minimize an open libre office document and then switch to a different program, and then click on the libre office icon that i have locked to the launcher, it just opens a NEW libre office document, not the one i already had open. and there doesn't seem to be an easy way to go back to whatever document i had open!

anyone have any ideas why it's doing this? i'm getting rather annoyed as this also means that if i have multiple documents open i don't have an easy way of switching between them (again, clicking on the libre office icon in the launcher just opens a new document instead of showing me the documents i already have open)

edited to add: OK - on a whim i just tried right clicking on the libre office icon and saw that apparently it WASN'T 'locked' to the launcher.... i clicked on 'lock to launcher' and now the icon displaying my active documents is showing up. 
yeah.

---

### Post by SheamusPatt on 2012-10-09
Same problem here. I'm running Unity with gdm, on an amd64 install. It's extremely annoying, especially when I'm trying to cut and paste between a web page and a document. 

If anyone has an idea what's going on (or better yet, a fix), I'd be extremely grateful!

---

### Post by spaceshipguy on 2012-10-11
Same problem. I have to use dash to search for an open document, because clicking the document's launcher icon does not find it. 

When I'm working on a document I often have a libre office icon that will open a new document, and a libre office writer icon that does  absolutely nothing and won't quit the application when I click quit. Right now the launcher integration of libre writer is just all messed up.
Grrr...

---

### Post by philinux on 2012-10-11
Odd this, seems fine here. Clean install beta 2 including home.

I'd suggest removing any OO config files from home first then resetting unity.

```
dconf reset -f /org/compiz/
```

---

