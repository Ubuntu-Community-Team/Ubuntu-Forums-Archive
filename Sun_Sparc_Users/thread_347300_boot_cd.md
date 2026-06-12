---
title: "boot cd"
date: 2007-01-27
forum: Sun Sparc Users
---

### Post by suessw on 2007-01-27
Hello

who knows which keys must hold down to get to the bios? 
My system won't boot from cd so I have to check bios first.

Thx

---

### Post by finer recliner on 2007-01-27
when you first turn on the computer, quickly look around the screen for a key to hit to enter BIOS setup or BOOT SEQUENCE (or something similar). my dell uses F12 or the delete key. try one of those.

and dont hold it down. tap the key very quickly until the menu loads.

---

### Post by Delta_Farce on 2007-01-28
For a Sun system you'll have to hit Stop-A during boot, and this will take you to the ok> prompt (which is the Sun OBP or bios equivalent).

If you don't have a Sun keyboard then it's a bit harder. With a Sunblade 100 or 150 you can get to the OBP by pressing the power button twice after the machine 'beeps' during startup. I don't know if this works for other Sun boxes though and you'll have to play with the timing of your button presses to get it right.

Have a look at this [Sun OBP Reference Card]("http://www.unixzone.dk/unix/sun/resources/SunOBP_Quick_Ref.pdf") as it should be useful and will tell you how to set boot devices and other things.

Cheers,

Mark

---

### Post by suessw on 2007-01-29
i will try this. Will let you know how this work for me.

thx

---

### Post by Moulton on 2007-02-02
The Sun Open Boot Monitor is similar to the one on the Macintosh and very unlike what you are used to on the x86 architecture.

There is a rudimentary HELP command at the Open Boot Prompt, but you are well-advised to read up on the documentation if you want to do anything more than issue a trivial boot command.

---

### Post by shoki on 2007-02-16
Thank for the info!

---

