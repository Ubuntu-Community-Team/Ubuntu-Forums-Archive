---
title: "[SOLVED] What happened to the battery % on the panel?"
date: 2017-09-12
forum: Ubuntu Development Version
---

### Post by Chanath on 2017-09-12
What happened to the battery % on the panel? 
It was there before on the top bar next to the battery icon, but not there any more. Can't find way to enable that again.
If there is a notification, when the battery reaches 95%, then I don't need it, but there are no such notification, and no way to enable it. If anyone knows how, please let me know. Thanks!

---

### Post by wgarcia on 2017-09-12
I'm still getting it. I'm using Unity in 17.10 alongside Gnome.

---

### Post by Chanath on 2017-09-12
> **wgarcia said:**
> I'm still getting it. I'm using Unity in 17.10 alongside Gnome.

In Unity, yes I have it. 
I have a partition with Gnome shell, and in that too I have it, but in the default Ubuntu installs, that useful % is gone. Would be nice to get it back.

---

### Post by Chanath on 2017-09-12
[COLOR=#696969][SIZE=3][FONT=arial]Okay, I got it back.
Used Dconf Editor, in  /org/gnome/desktop/interface/show-battery-percentage, changed it to true.[/FONT][/SIZE][/COLOR]

---

### Post by fthx on 2017-09-12
Or simply use Tweaks to do that...

---

### Post by Chanath on 2017-09-12
> **fthx said:**
> Or simply use Tweaks to do that...

True, but Tweaks is not default. In Unity that kind of convenience is default. If the devs are matching Unity look, at least some goodness of Unity must there too. :)

---

### Post by fthx on 2017-09-12
dconf-editor is not default too...

---

### Post by Chanath on 2017-09-12
> **fthx said:**
> dconf-editor is not default too...

Please read from [https://didrocks.fr/2017/08/14/ubuntu-gnome-shell-in-artful-day-1/](https://didrocks.fr/2017/08/14/ubuntu-gnome-shell-in-artful-day-1/)

---

### Post by fthx on 2017-09-12
(?)

---

### Post by Chanath on 2017-09-12
> **fthx said:**
> (?)
You'd know why Tweaks is not default etc...That's the guy, who is playing around with system extensions etc.

---

### Post by fthx on 2017-09-13
Ok but what's the point of your link here ?
Usual question, isn't it ?

---

