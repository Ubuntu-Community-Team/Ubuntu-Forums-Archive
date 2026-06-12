---
title: "Issues with GnuCash"
date: 2014-11-09
forum: Ubuntu/Debian BASED
---

### Post by dellwas on 2014-11-09
Installed GnuCash on a Zorin install of Ubuntu 14.04 on an e627 laptop, 64 bit.  Program loads and kicks out.

Here is what transpires when I enter gnucash at a command prompt.  Any ideas on how to correct this?

dellwas@dellwas-eMachines-E627:~$ gnucash
Gtk-Message: Failed to load module "overlay-scrollbar"
Backtrace:
In ice-9/boot-9.scm:
 157: 16 [catch #t #<catch-closure 26b73c0> ...]
In unknown file:
   ?: 15 [apply-smob/1 #<catch-closure 26b73c0>]
In ice-9/boot-9.scm:
3513: 14 [process-use-modules (((gnucash price-quotes)))]
 627: 13 [map #<procedure 2657c60 at ice-9/boot-9.scm:3513:25 (mif-args)> ((#))]
3514: 12 [#<procedure 2657c60 at ice-9/boot-9.scm:3513:25 (mif-args)> (#)]
2783: 11 [resolve-interface (gnucash price-quotes) #:select ...]
2708: 10 [#<procedure 264a580 at ice-9/boot-9.scm:2696:4 (name #:optional autoload version #:key ensure)> # ...]
2981: 9 [try-module-autoload (gnucash price-quotes) #f]
2320: 8 [save-module-excursion #<procedure 3aadc30 at ice-9/boot-9.scm:2982:17 ()>]
3001: 7 [#<procedure 3aadc30 at ice-9/boot-9.scm:2982:17 ()>]
In unknown file:
   ?: 6 [primitive-load-path "gnucash/price-quotes" ...]
In gnucash/price-quotes.scm:
  41: 5 [#<procedure 41e19a0 ()>]
In ice-9/boot-9.scm:
3513: 4 [process-use-modules (((www main)))]
 627: 3 [map #<procedure 2657c60 at ice-9/boot-9.scm:3513:25 (mif-args)> ((#))]
3514: 2 [#<procedure 2657c60 at ice-9/boot-9.scm:3513:25 (mif-args)> ((www main))]
2786: 1 [resolve-interface (www main) #:select ...]
In unknown file:
   ?: 0 [scm-error misc-error #f "~A ~S" ("no code for module" (www main)) #f]

ERROR: In procedure scm-error:
ERROR: no code for module (www main)
dellwas@dellwas-eMachines-E627:~$

---

### Post by deadflowr on 2014-11-09
*Thread moved to **Ubuntu/Debian BASED** sub forum*

Zorin is not Ubuntu, only based on Ubuntu.

---

### Post by dellwas on 2014-11-10
John Ralls, one of the developers gave me the solution when I reported it through Bugzilla:

rm -rf ~/.cache/guile/ccache/

---

### Post by jim_smith2 on 2014-11-24
> **dellwas said:**
> John Ralls, one of the developers gave me the solution when I reported it through Bugzilla:

rm -rf ~/.cache/guile/ccache/

Thanks so much for the answer to my problem.
Assuming it cropped up in a recent 
apt-get update or apt-get dist-upgrade

:popcorn:

---

