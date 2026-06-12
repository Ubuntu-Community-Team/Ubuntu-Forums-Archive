---
title: "Integrate &quot;extra buttons&quot; in mouse properties"
date: 2008-03-04
forum: Ubuntu Brainstorm
---

### Post by Bou on 2008-03-04
Hey guys, please take a look at this Idea and vote for it if you like it :)

[http://brainstorm.ubuntu.com/idea/3046/](http://brainstorm.ubuntu.com/idea/3046/)

I have just realised in Ubuntu Brainstorm ([http://brainstorm.ubuntu.com/idea/120/](http://brainstorm.ubuntu.com/idea/120/)) that a program called BTNX can help users who have a mouse with additional buttons get the most of their mice.

The interface to it, however, is quite complicated and not as simple as we would like for a Gnome app. It is quite undiscoverable, too, just because a user trying to configure their mouse is naturally going to look in system &#8594; preferences &#8594; mouse.

I think having a simplified frontend to BTNX in the mouse preferences menu would be the perfect solution. I have made a quick mockup:

[IMG]http://img254.imageshack.us/img254/3476/pantallazo1te7.png[/IMG]

As you can see, the interface is heavily influenced by the keyboard shortcut menu. The idea is, you hit "detect a button", then click the button you want to configure; then you can give it a name, an effect -key combination or command- specify the input for it.

---

### Post by keltren on 2008-03-10
Great idea - but there seems to be some support built into hardy now, at least I was able get the extra buttons on my mouse to work without the need for much fiddling (only thing I changed was adding: 
```
Option "Buttons" "9" 
```
to the mouse sections in xorg.conf and I'm not even sure if that was actually needed - have to check back). In "Advanced Desktop Effects Settings" I was then able to asign actions directly to Button 8 + 9 (in the "Rotate Cube" section I assinged rotate left/right to the 2 buttons).
See attachment for screenshot =>

Ofc having a tool to assign arbitrary keybindings to buttons is more flexible - but if you just want to control your desktop with the extra buttons compiz-fusion seems to be able to make use of those buttons without any extra software (personally I'm glad - btnx has always been sort of buggy for me)

Caveats:
- even if you're mouse only has 7 buttons (counting the scrollwheel as 2) the thumb buttons may be 8 and 9 (on my logitech g3 it's like this), starting "xev" in a console will help you figure out what your buttons are actually called.
- I first tried to bind the keys in the "viewport switcher" of the compiz settings, but for some odd reason clicks only seem to get registered if your mouse pointer is over the desktop (not a window). Setting it in Rotate Cube on the other hand always works.

I know this solution won't serve everbodies needs but I hope it saves a few people some unecessary fiddling around ;-)

---

### Post by Omnios on 2008-03-10
Dude this can be huge.
 
 I can see a lot of uses for developers and gamers. Keysets for programs such as Gimp etc and gamming has a lot of potential. 
 
 Only thing I would recomend would be a task bar app with different settings for different uses so you can say click and choose a set up for gimep and different games. Currently you can not use this in vista with a 5 button mouse so would give a linux advantage over other os's

---

### Post by greyfox1 on 2008-03-10
For the love of God YES!!!

I've spent countless hours trying to get full use of my buttons on my Logitech mx700 and so far, none of the solutions I've found have been a COMPLETE fix.  I would think a simple interface like this would be a no-brainer! :D

---

### Post by cszikszoy on 2008-03-12
Btnx is a great program to do this, but it would be awesome to have a cleaner integration inside of ubuntu.

---

