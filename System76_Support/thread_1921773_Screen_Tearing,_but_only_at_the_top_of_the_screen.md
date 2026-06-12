---
title: "Screen Tearing, but only at the top of the screen"
date: 2012-02-07
forum: System76 Support
---

### Post by Exüberance on 2012-02-07
Hi, I have an interesting problem: I have screen tearing, but ONLY on  the top of my screen. It's almost like the top 8% of my laptop is 1  frame behind.

It occurs in all applications, but to test it,  I  made a C++ program with xlib that just makes a small window that rapidly  switches from black to white.

I move it almost anywhere on the screen and it's fine- an image the switches between black and white really really fast.

But  if I move it to the top of the screen (about the first 85 pixels, but  most frequently probably around 60 pixels), there's awful tearing. The  tearing isn't always at the same pixel, but it's always within the first  85 lines of the screen.

I have a Gazelle Professional with  														Nvidia  GeForce GTX 560M. I'm running Oneiric with Compiz on GNOME Classic. By  using Compiz with vsync on and turning double buffering (flipping) off  in NVidia, I was able to eliminate horrible screen tearing everywhere,  but no matter what I do, I still always have screen tearing at the top  of my screen.

I am using the latest graphics drivers (version current-updates)

---

### Post by isantop on 2012-02-07
I would remove the Updates driver. They aren't recommended by Canonical, and we don't support them either. It will also be good to test on the other drivers.

Also, are you using 11.10?

---

### Post by Exüberance on 2012-02-07
I switched back to version-current, but still have the problem.
Yes, I am using 11.10 Oneiric. My account just says I use 9.10 because apparently the forum doesn't let you change that until you have 50 posts (wat?) so it still shown the first version of Ubuntu I used.


On a somewhat unrelated note, if I were to "down"grade back to Ubuntu 10.4, would it still be supported (or at least expected to work, including the graphics card)?

---

