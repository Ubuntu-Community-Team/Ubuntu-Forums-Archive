---
title: "Changing Ubuntu's login screen resolution?"
date: 2005-11-24
forum: The Cafe
---

### Post by nakedLefty on 2005-11-24
Hi guys, gonna try this post again.

Does any one here have any idea as to how one can change the resolution of the "login screen" for Ubuntu 5.10? 

I would like it very much to have the same resolution going on the "login screen" as my desktops resolution, and not as it is now where it's set to "max" resolution my screen or gfx card can handle.

Please help me Obi-ones, you are my only hopes :)

/nL

---

### Post by Pablo_Escobar on 2005-11-24
Issue this command in the terminal
sudo gedit /etc/X11/xorg.conf

Scroll down where You'll have 24 bits and below - the resolutions.
Erase the high ones (which You don't want to have) and as a first leave the one You want the login and desktop to have (mine's 1024x768 :( )

---

### Post by nakedLefty on 2005-11-24
Oh great thanks Pablo. 

Are you sad you cannot go any higher than 1024*768? I mean I'm just at the next stop 1152*864@85Hz on my Samsung SyncMaster 700NF - but it works fine for me :)

---

### Post by Pablo_Escobar on 2005-11-24
I've got and old CRT 17'' that can't go higher. I'll start saving for some nice LCD :)
Hope now login resolution is as You wanted it to be. :)

---

### Post by nakedLefty on 2005-11-24
Hurrah.... thank a bunch pEscobar, it worked like a charm, and looks soooooo much nicer than when it's "preassureing" my monitor/gfx card to the point where it just doesn't look nice or readable any more.

3 thumbs up Pablo, you're becoming my "go-to" guy! :)

/nL

BTW: CRT monitors rock... I mean I do "alot" of photoediting and homepage stuff here, and the "LCD"s that I have seen so far has not impressed me that much... well ofcourse the totally out of range priced ones look cool, but are out of range with that price tag.

---

### Post by Pablo_Escobar on 2005-11-24
Glad to be of service :)
In case You need help - PM me :)

---

### Post by nakedLefty on 2005-11-24
will do... you good looking guy you :)

---

