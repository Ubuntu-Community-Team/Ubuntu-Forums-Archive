---
title: "Compiz - Anyone else not able to move windows between workspaces"
date: 2013-03-12
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-03-12
when i launch compiz i can move a window across a workspace by dragging it there, but after i open a new window i cant do that anymore
you need to enable it in ccsm, 'disable grid' and in 'desktop wall' in the 'edge flipping' tab check the second box 'edge flip move'

---

### Post by dino99 on 2013-03-12
i suppose compiz will slowly die as Sam is gone now; and Mir is drawing a new story (and catch the main devs's time)

---

### Post by mc4man on 2013-03-12
Here there are 2 compiz things that tend to happen
1 is edge flipping with a window tends to break quite often, (I don't have grid enabled ever & use rotate instead of wall.
The easiest fix here when that happens is to edge flip an object (edge_dnd), then edge flip on windows starts up again.
(in the past there was an erroneous conflict between reveal left & edge flip but that seems taken care of, don't know when this current nonsense started...

Another longer standing issue is commands in the command plugin can just disappear on occasion, the binding(s) stay, commands go poof.

No workaround for that, I mainly use 1 very long command so instead have scripted it so easier to just re-enter scriptname
(re-enables in a fashion 'window picker for window group on ALL workspaces' which has been dead in compiz since unity started

---

