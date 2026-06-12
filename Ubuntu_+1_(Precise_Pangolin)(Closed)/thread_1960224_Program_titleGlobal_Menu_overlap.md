---
title: "Program title/Global Menu overlap"
date: 2012-04-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by The_Autonomist on 2012-04-17
This is relatively recent issue. First of all, my windo/program title and global menu overlap. Then, everytime i roll my mouse over the panel, the letters get thicker, darker, and more bold. if i click out of my window, it goes back to normal temporarily. Then, the letters turn black and bold all over again. It does this for every single program that i use. It's as if, rolling my mouse over the letters "boldens" them. 

Does anyone know how to fix this? I think it started happening after the recent Unity update.

I attached a screenshot of what my panel looks like.

---

### Post by mc4man on 2012-04-17
If you've set the panel to be fully transparent then you will see what is the 'Desktop app menu' in black. Sometimes it stays revealed, other times it disappears 
(will disappear if focus is returned to Desktop & stay gone untill a new window is opened or mouse over the panel

This is a fairly longstanding bug.
[https://bugs.launchpad.net/unity/+bug/924592](https://bugs.launchpad.net/unity/+bug/924592)

The previous workaround would be to set opacity to 0.0100, but that min. setting now produces a colored panel, this is a fairly new bug.
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/963505](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/963505)
 
Whether either one gets fixed before release is questionable.
Whether either ever get fixed in 12.04 don't know, hopefully at least one is, i suspect ultimately it won't be an issue in 12.10

---

### Post by The_Autonomist on 2012-04-17
Ah, okay. From now on, i'll make sure to search launchpad before making a post. 

But i just set the opacity to .0100 and it did produce a colored panel, but it'll have to do for now. Atleast the bolding/overlapping effect is gone. Hopefully they release a fix for one of these things. Thanks for the info!

---

