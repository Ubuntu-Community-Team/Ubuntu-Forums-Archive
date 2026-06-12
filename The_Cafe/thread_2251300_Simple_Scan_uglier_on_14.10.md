---
title: "Simple Scan uglier on 14.10?"
date: 2014-11-03
forum: The Cafe
---

### Post by The Cog on 2014-11-03
It seems to have lost the borders supplied by the desktop manager, and gone with its own ugly borders and menus. Completely ignoring the chosen theme.
Is this because they don't like unity stripping the menu off, or some other reason?

---

### Post by vasa1 on 2014-11-03
> **The Cog said:**
> It seems to have lost the borders supplied by the desktop manager, and gone with its own ugly borders and menus. Completely ignoring the chosen theme.
Is this because they don't like unity stripping the menu off, or some other reason?
Maybe it has to do with some gtk**3** apps having "client-side decorations": [http://blogs.gnome.org/mclasen/2013/12/05/client-side-decorations-in-themes/](http://blogs.gnome.org/mclasen/2013/12/05/client-side-decorations-in-themes/)

In such cases, the borders and decorations provided by the window manager may not be observed.

---

### Post by pqwoerituytrueiwoq on 2014-11-03
just tried to verify this in my virtualbox on 14.04
both lubuntu/Ubuntu boot in a unusable fashion
[[img]http://www.zimagez.com/miniature/screenshot-11032014-100909am.php[/img]](http://www.zimagez.com/zimage/screenshot-11032014-100909am.php)
you don't have to use simple scan *points at signature*

---

### Post by sffvba[e0rt on 2014-11-03
> **pqwoerituytrueiwoq said:**
> just tried to verify this in my virtualbox on 14.04
both lubuntu/Ubuntu boot in a unusable fashion
[[img]http://www.zimagez.com/miniature/screenshot-11032014-100909am.php[/img]](http://www.zimagez.com/zimage/screenshot-11032014-100909am.php)
you don't have to use simple scan *points at signature*

Had this issue with 14.10 just a little while ago.  Hit Ctrl[s]-Alt[/s] F1 and then Ctrl[s]-Alt[/s] F7...

edit: Make sure the virtual machine has focus...

---

### Post by pqwoerituytrueiwoq on 2014-11-03
simple scan looks norm in ubuntu,definably the change to gtk3 i would assume based on how it looks in lubuntu
in VB it is right control F1 then right ctrl F7

---

### Post by The Cog on 2014-11-03
Oh well. That's the last straw with simple-scan. For something that simple, it shouldn't take that much clicky-clicky to choose the scan resolution before scanning. 
It's a relief to install xsane.

I hope we don't see lots of other apps going ugly like that.

---

### Post by pqwoerituytrueiwoq on 2014-11-03
> **The Cog said:**
> Oh well. That's the last straw with simple-scan. For something that simple, it shouldn't take that much clicky-clicky to choose the scan resolution before scanning. 
It's a relief to install xsane.

I hope we don't see lots of other apps going ugly like that.
now that i agree with
you may want to take a look at the web based UI i made (link in signature)
*the screenshots in the wiki are out of date

---

