---
title: "Stuttering in games (wow, minecraft) (not WINE)"
date: 2011-02-09
forum: Wine
---

### Post by AdamGM on 2011-02-09
Greetings all,

I've been noticing a stutter in my games. In WoW I notice it most when walking, it is like a small stutter backwards (like someone is hitting the back of my monitor), it's slight but noticeable.

At first I thought this was an incompatibility with wine issue, but I've also noticed it in the Linux version of minecraft. As the stars, for example, move across the sky they stutter backwards (in their path) every few seconds.

I'm using the 3d accelerated drivers for my Radeon 4350. Quad core i5, 4GB memory, 64bit version of Ubuntu 10.10

Please help!

---

### Post by mitchej123 on 2011-02-09
Try turning off CPU scaling or setting it to performance instead of ondemand.  There should be a cpufreq applet you can add to your bar in gnome.

---

### Post by AdamGM on 2011-02-09
Thanks for the reply. I'm fairly new to Ubuntu, both of those things can be done through an applet?

---

### Post by AdamGM on 2011-02-09
I see it. Is there any reason I wouldn't want to keep it on performance? (For my PC)

---

### Post by AdamGM on 2011-02-09
Didn't seem to make any difference in Minecraft. It even looks like the frequency of the stutter increased.

---

### Post by mitchej123 on 2011-02-09
Performance keeps it running at full speed, ondemand tries to intelligently scale back the CPU when it's not needed and clock it up again when it is needed (Except it seems to have some problems with 3d games like you're noticing).  

I've usually kept mine ondemand unless I had a reason to change it.  Lower CPU frequency would consume slightly less power and generally produce less heat.

---

### Post by AdamGM on 2011-02-09
Sorry, added one more post just a moment before you did :) Didn't seem to help.

---

### Post by mitchej123 on 2011-02-09
> **AdamGM said:**
> Didn't seem to make any difference in Minecraft. It even looks like the frequency of the stutter increased.

I haven't played with Minecraft, I only noticed this problem when I used to play Wow and it seemed to solve it for me.  If that didn't help I'm afraid I don't have any other ideas off the top of my head.

---

