---
title: "Beta 2 Quick First Look"
date: 2012-03-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Jerry N on 2012-03-29
My quick look at Beta 2 Live:  Sharing with Windows 7 with Samba worked OK.  This is a surprise since I have been having trouble with this in Ubuntu for some time (But no trouble in Mint).  I don't like the buttons on the left side and I still don't like the silly non-sliders.  I couldn't find the terminal. I am downloading Lubuntu 12.04 Beta 2 as I type this and will see how it looks to me.  

Jerry

---

### Post by craig10x on 2012-03-29
> **Jerry N said:**
> My quick look at Beta 2 Live:  Sharing with Windows 7 with Samba worked OK.  This is a surprise since I have been having trouble with this in Ubuntu for some time (But no trouble in Mint).  I don't like the buttons on the left side and I still don't like the silly non-sliders.  I couldn't find the terminal. I am downloading Lubuntu 12.04 Beta 2 as I type this and will see how it looks to me.  

Jerry

Hint: to find terminal in Unity...open the "dash" (search) type the letter t
and the terminal is the first item you see...

use terminal frequently? want one click access?  pin it it to the unity bar
(while terminal is open and showing in the unity bar,  right click and select "keep in launcher") done...

---

### Post by cariboo on 2012-03-29
I'm surprised how many people haven't embraced the search function in menus, Windows has had it since Vista, and I'm not sure how long it's been in OSX, as my PPC iMac isn't supported any more, it's running OSX 10.4, but it works there too.

---

### Post by jerrylamos on 2012-03-29
> **Jerry N said:**
> My quick look at Beta 2 Live:  Sharing with Windows 7 with Samba worked OK.  This is a surprise since I have been having trouble with this in Ubuntu for some time (But no trouble in Mint).  I don't like the buttons on the left side and I still don't like the silly non-sliders.  I couldn't find the terminal. I am downloading Lubuntu 12.04 Beta 2 as I type this and will see how it looks to me.  

Jerry

One of the first things after an install is to put buttons back on the right with this exec

$!/bin/bash				
gconftool-2 --set /apps/metacity/general/button_layout --type string menu:minimize,maximize,close
exit 0

Ctrl-Alt-t will get you a terminal, then right click on the resulting launcher button and lock to the launcher if you like.  On lubuntu, it's easy to put on the panel no fussy launcher.

Have fun.

Jerry

p.s. installed Beta 2 on 4 different test pc's over the last couple days.  Some bugs no showstoppers.

---

