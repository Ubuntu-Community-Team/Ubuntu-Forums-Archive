---
title: "Blocky fonts in Office 2007"
date: 2009-02-05
forum: Wine
---

### Post by turinturambar on 2009-02-05
I'm running Office 2007 under wine 1.12(I think) and everything works very nicely EXCEPT small fonts.  To make fonts appear smooth instead of pixelated, I have to either crank up the dpi ridiculously high in wine configuration, or else put the word window at 140%.  I don't like either option very much.

I think it's supposed to work if I have the right freetype library.  How do I get the right one, and how do I fix my ugly fonts?  This is one of two reasons I still have a windows partition, and it's the main one.  If anyone could help, that would be great.

Thanks!

---

### Post by cogadh on 2009-02-05
Not sure if this would make a difference, but have you installed the msttcorefonts package?

---

### Post by mashiox on 2009-02-05
Have you considered installing OpenOffice?
It's MS Word compatible and functions the same way if not better.

---

### Post by turinturambar on 2009-02-05
I already have msstcorefonts.  I've checked half a dozen times.

I have openoffice, but I prefer to use office 2007.  Compatibility is sometimes an issue, and I think that the ribbon interface is much better and cleaner than office 2003's and openoffice's endless menus.

Can anybody help me?

Thanks

---

### Post by lykwydchykyn on 2009-02-05
I had this problem, I think it's a conflict with the Nvidia driver I'm using.   The fix is in this thread:

[http://ubuntuforums.org/showthread.php?t=1009930](http://ubuntuforums.org/showthread.php?t=1009930)

That  worked for me.  good luck!

---

### Post by turinturambar on 2009-02-06
Neither the registry edit or the driver thing worked.  I still have fonts as ugly as sin.  Thanks though.

When I open wineconfig, the fonts are fine there.  Nice and readable and everything.  The problem is just the fonts that are typed WITHIN word documents.

I think it has something to do with my freetype library, but I barely know what freetype is let alone how to use it to enable subpixel font rendering.  Does anybody know anything about this?

Thanks

---

