---
title: "Aspire-E5-575G, gnome. One cpu core works 100%"
date: 2017-11-25
forum: Ubuntu/Debian BASED
---

### Post by bersp on 2017-11-25
[IMG]https://imgur.com/A7qKy0N[/IMG]Hi, Im Bernardo.
This is my first post, Im from Argentina, sorry if my english is to bad.
Recently I pass my pc from Ubuntu 16.04 LTS to Ubuntu 17.10, and later to ElementaryOS. With this last two I have the same problem, that why I think that the problem is gnome.
I tryed to remove intel drivers and reinstall and the problem continues.

[https://imgur.com/A7qKy0N](https://imgur.com/A7qKy0N)
[IMG]https://imgur.com/A7qKy0N[/IMG]
[IMG]https://imgur.com/A7qKy0N[/IMG][IMG]https://i.imgur.com/A7qKy0N.png[/IMG]

---

### Post by Yellow Pasque on 2017-11-26
```
sudo apt-get install htop
htop
```

Click on "CPU%" to sort the list and see what processes use the most CPU.

Note: I guess you can do the same thing in System Monitor, but I don't trust it. I've seen it spike the CPU itself too many times.

---

### Post by bersp on 2017-11-26
[IMG]https://i.imgur.com/aQTYvax.png[/IMG]
Thanks to reply! This is what show. Usually is the core 3 the one who do that, but in my firs post is the 1.

---

### Post by Yellow Pasque on 2017-11-26
Your screenshot shows one core at 19% and the other cores at < 3%. In other words, no issue/problem.
Check htop periodically to see if it shows high CPU utilization at idle and then take a screenshot of that.
If htop never shows high CPU at idle, then it's the System Monitor GUI that is causing the spike (or reporting incorrectly).

---

### Post by bersp on 2017-11-26
[IMG]https://i.imgur.com/7ahnXbE.png[/IMG]
I dont know how to describe it, but I feel the PC a little bit slow. The animations are no fluid, and they match in time with the spikes.
Also, I have a friend who have almost the same pc (2017 with Intel 7gen, and  I have 2016 Intel 6gen) and I dont feel that slow in his pc. He have Elementary OS too and the Gnome Monitor reports normal in his PC.

---

### Post by howefield on 2017-11-26
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

