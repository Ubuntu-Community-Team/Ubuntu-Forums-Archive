---
title: "Files 3.10 (Nautilus) fudging doc names"
date: 2014-03-30
forum: Ubuntu Development Version
---

### Post by mayagrafix on 2014-03-30
Just upgraded to 14.04 and Files 3.10 will replace document names with 3 dots
[[IMG]http://i16.photobucket.com/albums/b1/mayagrafix/binaryes/Filesmissingnames_zpsed8fa371.png[/IMG]](http://s16.photobucket.com/user/mayagrafix/media/binaryes/Filesmissingnames_zpsed8fa371.png.html)

---

### Post by coffeecat on 2014-03-30
*Thread moved to **Ubuntu +1**.*

---

### Post by mc4man on 2014-03-30
Stick your cursor on the little bar | to the left of "Size" and drag to the right to increase size of "Name" column

---

### Post by mayagrafix on 2014-03-30
Thanks, good call. The little bar | is frozen and will not drag even though the double sided arrow appears. I tried that and double clicking it to reset size of name colum and no joy.

---

### Post by mc4man on 2014-03-30
I would log in to the guest session (or create a new user account to test) & see if resizing works there.

---

### Post by mayagrafix on 2014-03-30
Did the new user account thing and resize works well. The problem seems to happen when I use the find button, as long as its open, the names colum reduces in size knocking out the names. When turn off the find button (one with the magnifying glass icon), doc names go back to normal.

---

### Post by mc4man on 2014-03-30
> **mayagrafix said:**
> Did the new user account thing and resize works well. The problem seems to happen when I use the find button, as long as its open, the names colum reduces in size knocking out the names. When turn off the find button (one with the magnifying glass icon), doc names go back to normal.
That doesn't seem to be an issue here as long as there is nothing entered in the search bar. After doing a search the columns do 'shrink' (move to left), but here not as far as you're showing . (though the shrinking feels like a bug or could be search can't have all the columns normal list mode can...

Maybe try making your icons smaller in list view -  >  Edit > Preferences > List View defaults > Default zoom level

On the other hand if you get Search as a location then nautilus becomes somewhat or completely  borked & resizing doesn't work. (among other things
 Hard to explain, see screen & notice the breadcrumb is just "Search"
(- search as a location  is not the same as not entering a search term yet.

---

