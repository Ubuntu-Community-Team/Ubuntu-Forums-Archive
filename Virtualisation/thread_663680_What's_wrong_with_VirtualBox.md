---
title: "What's wrong with VirtualBox?"
date: 2008-01-10
forum: Virtualisation
---

### Post by CCBalla10 on 2008-01-10
ok, so I go and set up my VirtualBox with Windows XP and got it working...then I go to use it today and it doesn't ever load.  I took a video of it in action check it out.  Anyone know what's wrong?



[http://www.youtube.com/watch?v=0ZzLQiqogLU]("http://www.youtube.com/watch?v=0ZzLQiqogLU")

---

### Post by daniel_szollosi-nagy on 2008-01-10
Hmm Windows appears to die just as it tries to switch to a desktop resolution. It'd say you probably installed a display driver specific to the video card in your PC. Alas, VirtualBox uses a different video card and forcing that driver may have nuked the setup. Try restarting Windows in safe mode and remove that driver.

The problem is not related in VirtualBox in a way that it does what a normal Windows would do when subjected to the same :D

---

### Post by Cyris on 2008-01-12
I think you hit the nail right on the head because I've done that before trying to run quake 3 in a virtual XP and it did the same thing. dont install any drivers in a virtual XP its just gonna break it.

---

