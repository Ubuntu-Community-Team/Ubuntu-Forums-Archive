---
title: "Plainshift in Hardy - LinuxClient"
date: 2008-03-08
forum: Ubuntu Gamers Arena
---

### Post by ozelot on 2008-03-08
**EDIT: The game's name is Planeshift though ...**

Whenever the inventory or i guess generally inventory icons come into play the client crashes. 
I already tried to substitute some of the files in the game's lib folder from my system /usr/libs folder, but then discovered this when starting from console:
[...]
[B]crystalspace.graphics3d.shader.fixed:
  Multitexture units: moderate 4
   78604) <src/client/charapp.cpp:470 ChangeMaterial>
   78605) Failed to set material "/planeshift/models/dermf/dermf_hand_chainmail.dds" on part "Hand"
Aborted (core dumped)[/B]
This looks actually not very complex, but I for sure have no idea how to fix this. :confused:
**For ref.:** The win client -under wine- does load inventory properly. Neither does it crash on give or loot... But unfortunately the menues and all buttons are invisible which makes things difficult :(
   
Any sugg. welcome!
regards,
oz

---

### Post by ozelot on 2008-03-18
(Unconfirmed) workaround to be found here:
[http://hydlaa.com/smf/index.php?topic=31815.msg366362#msg366362]("http://hydlaa.com/smf/index.php?topic=31815.msg366362#msg366362")
I hope it helps.

Cheers,
oz

---

