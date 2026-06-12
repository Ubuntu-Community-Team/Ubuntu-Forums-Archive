---
title: "Graphics still to slow after adding 3D acceleration in Ubuntu 13.04 guest"
date: 2013-07-10
forum: Virtualisation
---

### Post by groundnut on 2013-07-10
I have installed an Ubuntu 13.04 Guest in an Ubuntu 13.04 Host machine.
At first the graphics were very slow. (By the way I have a discrete Nvidia graphics card).
Then I added 3D acceleration (see picture below).
Now the machine is just a little bit to slow.

What can I do to improve the graphics?

[ATTACH=CONFIG]244585[/ATTACH]

---

### Post by TenPlus1 on 2013-07-10
You have to be more specific with your computer specs, graphics card, wether you are running Ubuntu in a virtual box guest setup ?

---

### Post by groundnut on 2013-07-11
My Ubuntu 13.04 host machine: 
Intel Core 2 Quad Q8200 processor
Nvidia Geforce 9600 GT graphics card
4 GB RAM

My Ubuntu 13.04 guest machine running in a virtual box:
Basic Memory 512 MB
Video Memory 128 MB
3D acceleration activated

---

### Post by crjackson on 2013-08-30
I'm not exactly sure how you're defining just a little bit slow, but your vm settings look like it's memory starved. Bump up the memory (double it) and try again.

---

### Post by groundnut on 2013-09-03
I augmented the basis / RAM memory to 1024 MB. This made the video more fluent.
Augmenting the memory to 1505 MB increased the fluency again.

Though there is improvement, it is not sufficient.

Any suggestions?

---

