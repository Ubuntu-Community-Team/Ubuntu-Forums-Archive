---
title: "Remove &quot;Wine core exe&quot; in &quot;Open with&quot; menu"
date: 2011-01-05
forum: Wine
---

### Post by tranduyhung on 2011-01-05
Hi,

I uninstalled Wine. But when I right click on files, I still can see "Wine core exe" in "Open with..." menu. You can see the screenshot if you don't understand (sorry for my English :))

How could I get rid of this?

Thanks!

---

### Post by RigelAlien on 2011-02-04
I had this problem too.

This article:  [http://www.lffl.org/2011/01/ubuntu-rimuovere-wine-core-exe-dal-menu.html#more](http://www.lffl.org/2011/01/ubuntu-rimuovere-wine-core-exe-dal-menu.html#more)

Says to remove your mimeinfo.cache, e.g.:

[INDENT]     rm /home/$USER/.local/share/applications/mimeinfo.cache
[/INDENT] 
And re-start Nautilus

[INDENT]     nautilus -q
[/INDENT] 
This worked for me!

):P

---

### Post by autofyrsto on 2011-03-06
Worked for me, also. :)

---

### Post by phoros on 2011-03-22
And this is what I love in Ubuntu community: first google's answer and the problem's solved. Thanks!

---

