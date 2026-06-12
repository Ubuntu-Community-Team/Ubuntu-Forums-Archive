---
title: "Gnucash fails to start on Gnome 15.04"
date: 2015-03-13
forum: Ubuntu Development Version
---

### Post by crcarson on 2015-03-13
Tried to start gnucash and got the following output.

Traceback (most recent call last):
  File "/usr/share/gnucash/python/init.py", line 3, in <module>
    from gnucash import *
ImportError: No module named gnucash
Backtrace:
In ice-9/boot-9.scm:
 157: 16 [catch #t #<catch-closure 1409a20> ...]
In unknown file:
   ?: 15 [apply-smob/1 #<catch-closure 1409a20>]
In ice-9/boot-9.scm:
3597: 14 [process-use-modules (((gnucash price-quotes)))]
 702: 13 [map #<procedure 13a8ee0 at ice-9/boot-9.scm:3597:25 (mif-args)> ((#))]
3598: 12 [#<procedure 13a8ee0 at ice-9/boot-9.scm:3597:25 (mif-args)> (#)]
2864: 11 [resolve-interface (gnucash price-quotes) #:select ...]
2789: 10 [#<procedure 139b800 at ice-9/boot-9.scm:2777:4 (name #:optional autoload version #:key ensure)> # ...]
3065: 9 [try-module-autoload (gnucash price-quotes) #f]
2401: 8 [save-module-excursion #<procedure 2ee4f30 at ice-9/boot-9.scm:3066:17 ()>]
3085: 7 [#<procedure 2ee4f30 at ice-9/boot-9.scm:3066:17 ()>]
In unknown file:
   ?: 6 [primitive-load-path "gnucash/price-quotes" ...]
In gnucash/price-quotes.scm:
  41: 5 [#<procedure 1e002e0 ()>]
In ice-9/boot-9.scm:
3597: 4 [process-use-modules (((www main)))]
 702: 3 [map #<procedure 13a8ee0 at ice-9/boot-9.scm:3597:25 (mif-args)> ((#))]
3598: 2 [#<procedure 13a8ee0 at ice-9/boot-9.scm:3597:25 (mif-args)> ((www main))]
2867: 1 [resolve-interface (www main) #:select ...]
In unknown file:
   ?: 0 [scm-error misc-error #f "~A ~S" ("no code for module" (www main)) #f]

ERROR: In procedure scm-error:
ERROR: no code for module (www main)

Remove gnucash and reinstalled it looking for any errors reported during the install but saw nothing.

---

### Post by PhilGil on 2015-03-13
Have you tried the fix from [this Debian bug report]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=764821") and deleted your *~/.cache/guile/ccache/* folder?

---

### Post by crcarson on 2015-03-14
> **PhilGil said:**
> Have you tried the fix from [this Debian bug report]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=764821") and deleted your *~/.cache/guile/ccache/* folder?

Yes, deleting the ccache folder did it, thanks.

---

