---
title: "emacs 22 in backports ?"
date: 2007-06-10
forum: Repositories &amp; Backports
---

### Post by shomati_sen on 2007-06-10
Hi,

I'd like to request the newly released Emacs 22 as part of Feisty backports.

Thanks,

Shomati

---

### Post by mopi on 2007-06-24
I'll second that.

---

### Post by nigeldgreen on 2007-06-25
I'll third that. I've tried to install from sources but it seems to trip over a termcap entry.  I've also tried apt-get install emacs-snapshot-gtk, which launches and appears to run fine but trips over some entries in my .emacs and doesn't play nicely with planner-mode.

Any tips on getting the snapshot working would be very gratefully received...

Nigel

---

### Post by posco on 2007-07-21
I'll add my voice to the call for Emacs 22 as well!

---

### Post by posco on 2007-07-21
nigeldgreen: I didn't have any problem compiling emacs-22.1 from source. I just installed a bunch of the *-dev packages related to the libraries emacs was trying to find when doing ./configure (libgtk2.0-dev, libpng12-dev, etc..) and ran ./configure --with-gtk && make and everything seemed to work. No termcap problems.

---

### Post by vambo on 2007-07-21
> **posco said:**
> I'll add my voice to the call for Emacs 22 as well!

And me ... yet again. Inquired about this ages ago, not a whimper

---

### Post by daveluciffer on 2007-07-23
You can install the newest version by 
(1) extract package
(2) ./configure
(3) check if there are any header or dev repositories missing for building, especially support for X
(4) sudo make
(5) sudo make install
(6) install the newest version of cedet, ecb
(7) make changes in your .emacs file


for no termcap problem, search "termcap" in the app manager, and then install the dev repo that are supported by ubuntu, then 
make distclean
./configure
sudo make
sudo make install

You should be fine after that.

---

