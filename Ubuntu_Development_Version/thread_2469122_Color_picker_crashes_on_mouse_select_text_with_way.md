---
title: "Color picker crashes on mouse select text with wayland"
date: 2021-11-20
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2021-11-20
This only happens with wayland when using this color picker with the widget, it will not crash when run via plasmawindowed
i tried to record the screen with kazam and all i got was a black video

this is the widget i am using:
[https://github.com/wsdfhjxc/do-it-yourself-bar](https://github.com/wsdfhjxc/do-it-yourself-bar) (compile/install instruction work no problem)

after adding the widget to the panel/desktop
[LIST=1]
[*]right click
[*] configure
[*]appearance
[*]under block indicators  check a box -> click the color picker (colored square) (as long as you enable a checkbox that lets you use the color picker it does not matter)
[*]highlight one/part of the color's 3 digit number(s) (hue/sat/val/red/green/blue) using the mouse (does not crash w/ keyboard)
[*]insta-crash and it takes the panel out with it
[/LIST]
no idea how to report this one

---

### Post by pqwoerituytrueiwoq on 2021-11-21
so it seems that OBS can record wayland

[https://mega.nz/file/1U9AVIjb#G1gAyiJ4Y52BjAAp2S1PKUUhZ9_d7XC9hrpxF8gvOHo](https://mega.nz/file/1U9AVIjb#G1gAyiJ4Y52BjAAp2S1PKUUhZ9_d7XC9hrpxF8gvOHo) 3.3Mib 1 min 41 seconds

seems mega is broken in firefox... this is why i like having a second browser for, glad edge does not use snap

[https://www.mediafire.com/file/oo7ye53z6fu9vr5/2021-11-21+08-27-21.mkv/file](https://www.mediafire.com/file/oo7ye53z6fu9vr5/2021-11-21+08-27-21.mkv/file) (i'm guessing this link will expire eventually)

also notice how hard of a time i had clicking the context menu, not a issue in X11

---

