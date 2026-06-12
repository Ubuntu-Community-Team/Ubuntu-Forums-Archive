---
title: "Unicode Input for LibreOffice in Xubuntu"
date: 2011-07-17
forum: Tutorials
---

### Post by melander on 2011-07-17
If you're trying to input a non-keyboard character in Xubuntu, you hit [Ctrl]+[Shift]+u, then type in the four digit Unicode hex digit for your character and then hit enter.

This is needed not only for foreign language words but also for typographical characters such as section (§ [Ctrl]+[Shift]+u 00a7 [Enter]), paragraph (¶ [Ctrl]+[Shift]+u 00b6 [Enter]) or a proper "en" dash (— [Ctrl]+[Shift]+u 2014 [Enter]).

Libreoffice Write wasn't allowing me to do this. The problem turned out to be that I didn't have the libreoffice-gtk package installed.

Hope this helps somebody.

Regards,

---

### Post by Ranko Kohime on 2011-10-09
> **melander said:**
> ...or a proper "en" dash (— [Ctrl]+[Shift]+u 2014 [Enter]).

Hope this helps somebody.
This has helped me, thank you.  :)

Oh, and 2014 is an "em" dash.  ;)

---

### Post by Headwreck on 2012-01-13
Thanks from me, too!  That tip about libreoffice-gtk is a winner :)

---

### Post by GOwin on 2012-05-10
> **melander said:**
> Libreoffice Write wasn't allowing me to do this. The problem turned out to be that I didn't have the libreoffice-gtk package installed.

Hope this helps somebody.

Regards,

Just experienced the same issue with Calc. Thank you for sharing this informative post. 

However, after I installed gtk-office Calc would  display the unicode character as a box in the input line.

---

