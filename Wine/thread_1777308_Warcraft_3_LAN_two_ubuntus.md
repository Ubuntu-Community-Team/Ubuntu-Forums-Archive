---
title: "Warcraft 3 LAN two ubuntus?"
date: 2011-06-07
forum: Wine
---

### Post by RichardC400 on 2011-06-07
This is only a query about this now but I just wanted to know for future reference.

I have Warcraft 3 RoC installed succesfully and everything runs smoothly. (i can't find my tft lol)

I LANed three computers (my ubuntu, xp, vista) together perfectly.
This was after I read that the Ubuntu game could not host one for the other two.
Does this mean that if i convert my xp to ubuntu i wont be able to host a game on that even if it was only a LAN between two ubuntus?

if that makes sense

---

### Post by RichardC400 on 2011-06-12
Bump, still curious

---

### Post by dacha on 2011-06-13
You might need to add a route for the 255.255.255.255/32 address Warcraft uses for LAN broadcasts, because this works on Windows but not on Linux:

sudo route add -net 255.255.255.255 netmask 255.255.255.255 dev eth0

Also I find that you sometimes need to restart Warcraft on Linux after each LAN game.

But otherwise mixed Windows/Linux LAN games just work.

---

### Post by RichardC400 on 2011-06-13
Ah i see, thank you, i don't really mind restarting after every LAN game, i was just a little unsure.

---

