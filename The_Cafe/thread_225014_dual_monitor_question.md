---
title: "dual monitor question"
date: 2006-07-28
forum: The Cafe
---

### Post by briancurtin on 2006-07-28
im not much of a hardware guy at all and dont really know much about dual monitors...but my last two jobs and current job have supplied me with them, and i know that i love them. however, i dont know if this card will work for dual monitors...or if there are certain cards that work for dual and some that dont.

im about to buy a dell that comes with...
this card: 256MB PCI Express™ x16 (DVI/VGA/TV-out) ATI Radeon X600 SE HyperMemory
two of these dell monitors: [http://accessories.us.dell.com/sna/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=320-4568](http://accessories.us.dell.com/sna/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=320-4568)

id like to have an nVidia card, but thats not an option on this box. i could do that afterwards, but if this ATI card can do dual monitors and work, then id like to stik with it.

the big question is: can i make it work, and if not, what do i need to do to make it work.

---

### Post by scxtt on 2006-07-28
more or less any card that has multiple outs (VGA, DVI, s-video) will work in a dual monitor setup ... i have an ATI x850Pro and use dual 1600x1200 (or 3200x1200) ... it also worked w/ xinerama, but i wasn't happy w/ the way it performed ...

---

### Post by briancurtin on 2006-07-28
how long did it take you to get that setup? ive been reading that some people have had a good bit of trouble with it but got it working after a long time...which isnt a problem, im just wondering

---

### Post by scxtt on 2006-07-28
i did it again last night - after a reinstall of dapper ... i'd been acustomed to using ATI's 8.24.8 drivers, but for some reason it was giving me hell last night and had to use [8.26.18](http://www.ubuntuforums.org/showthread.php?t=204910) ... that went reasonably well and i attempted my usual method for dual-screen, didn't work - luckily i had an 'old' xorg.conf i'd set up for dual-screen --- swapped them out and did a ctrl+alt+backspace and had my 3200x1200 ...```
aticonfig --initial=dual-head --dtop=horizontal --screen-layout=right --iagp=off -v
/etc/init.d/gdm restart
```

---

### Post by briancurtin on 2006-07-28
cool, thanks man. i think im going to go for it and get the two monitors

---

### Post by scxtt on 2006-07-28
go for it! :) ... i'm so used to it now, that the thought of not using 2 makes me 'sad' ... even if you do have initial issues, i'm sure it can be worked through ...

---

### Post by djsroknrol on 2006-07-29
I'm running a Radeon 9200SE dual monitor setup with the OSS "Radeon" driver...haven't had a problem with it and it was a snap to set up...I'll post my xrog.conf if you need it..

---

### Post by briancurtin on 2006-08-02
i got my computer yesterday and got it all setup on my desk and stuff late last night but just left windows on there for the night since i had to get some rest for work. i came home today, installed Arch, and it only took me 4 tries i think to get dual monitors working correctly. now i have two 19" monitors side-by-side working beautifully :-)

ill take a screenshot once i get a wallpaper and stuff, i just got it setup like 2 minutes ago

---

### Post by briancurtin on 2006-08-02
edit: double post

---

