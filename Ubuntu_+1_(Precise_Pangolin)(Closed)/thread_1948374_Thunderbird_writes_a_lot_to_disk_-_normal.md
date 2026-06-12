---
title: "Thunderbird: writes a lot to disk - normal?"
date: 2012-03-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by MacUntu on 2012-03-28
I've been running `sudo iotop -a` for the past two hours and with a polling time of one minute, thunderbird-bin has written 120 MiB to disk. Is that normal? I only got like 10 mails during that time...

Here's example output from fatrace, showing writes during **one** mail check:

> 11:59:51.507626 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.507738 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.507794 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.507908 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.507965 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.508079 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.508132 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.508240 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.508293 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.508386 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.508475 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.508535 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.508613 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.508697 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.508776 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.508856 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.508936 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.509034 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.509117 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.509196 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.509275 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.509355 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.509434 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.509512 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.509590 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.509669 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.509747 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.509827 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.509906 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.509984 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.510060 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.510140 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.510218 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.510297 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.510375 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.510452 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.510529 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.510606 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.510682 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.510760 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.510836 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.510915 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.510992 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.511069 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.511144 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.511220 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.511298 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.511373 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.511448 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.511524 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.511601 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.511677 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.511753 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.511829 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.511904 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.511986 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.512061 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.512136 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.512212 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.512286 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.512362 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.512437 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.512511 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.512588 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.512664 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.512738 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.512814 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.512889 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.512964 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.513051 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.513125 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.513200 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.513274 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.513349 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.513423 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.513496 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.513571 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.513646 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.513720 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.513794 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.513868 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.513943 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.514017 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.514093 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.514168 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.514241 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.514315 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.514372 thunderbird-bin(15490): CW /.../my-pop-account/popstate.dat
11:59:51.514674 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.514747 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.514822 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.514896 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.514968 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.515042 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.515114 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.515187 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.515262 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.515334 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.515407 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.515481 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.515554 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.515630 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.515703 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.515777 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.515851 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.515924 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.515997 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.516070 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.516142 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.516216 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.516290 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.516362 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.516436 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.516508 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.516582 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.516657 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.516731 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.516804 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.516876 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.516951 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517047 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517121 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517165 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517198 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517230 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517263 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517295 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517328 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517361 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517394 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517427 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517459 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517492 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517524 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517557 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517589 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517621 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517654 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517687 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517719 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517752 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517785 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517817 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517851 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517883 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517916 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517949 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.517980 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518013 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518046 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518078 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518111 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518143 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518176 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518208 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518240 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518273 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518307 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518339 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518371 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518403 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518436 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518469 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518501 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518533 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518566 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518598 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518630 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518663 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518703 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518736 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518772 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518806 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518839 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518873 thunderbird-bin(15490): W /.../my-pop-account/popstate.dat
11:59:51.518898 thunderbird-bin(15490): CW /.../my-pop-account/popstate.dat

Is that normal?

---

### Post by kelpdip on 2012-03-28
Account Settings - Sync/Storage
The default value tried to download my entire gmail. Maybe check here?
Nevermind, it doesn't look like that's showng up in fatrace.

---

### Post by MacUntu on 2012-03-28
It's checking the mail (without anything to download) that's causing almost 1 MB written to disk. Since I check it every minute that's over 1 GB per day!

---

### Post by mc4man on 2012-03-28
Probably unrelated but yesterday when experiencing some updated related difficulties saw 10's of thousands  of TB lines in xsession-errors (had swelled the file to around 70k lines
No longer seeing anything related today, have updated all thru proposed
(where are these writes going to?

---

### Post by clifford junior on 2012-03-29
i dont know if this is related or not but today i was writing a rather long email and was saving it periodically.

then when i sent it it sent 44 times and sent every draught copy. is this normal behaviour of how draft works?

---

