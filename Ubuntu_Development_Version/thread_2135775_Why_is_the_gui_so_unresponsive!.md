---
title: "Why is the gui so unresponsive!"
date: 2013-04-15
forum: Ubuntu Development Version
---

### Post by davidmit on 2013-04-15
Hi guys, hoping to get a steer as to what my problem is. 

I have installed Ubuntu 13.04 on my work laptop as an OS to play about with.

The laptop is a beast its an Elitebook 8570w, Intel I7, 32GB memory and Nvidia Quadro T2000m.

Strange thing is that performance is appalling. When I click firefox it waits for ~ 10 seconds before opening.

If I change tty and run apt-get update it takes an age to retrun to the prompt.


Something is seriously holding things up but I've no idea what. Its certainly not swapping, and running top doesnt really show anything running on the 8 virtual cores.

I guess its not the video card, as even just on a text tty it is slow. Running a benchmark returns a fast result, it is just very unresponsive to start.

Windows runs nice and fast, so I'm stumped.

Thoughts?? Should I downgrade to v12?

---

### Post by dino99 on 2013-04-15
Glance at .xsessionèerrors & xorg.0.log to find possible usefull warnings/errors.
Are you sure your quadro is well recognized ? (watch System Settings)
You should use the latest nvidia driver (319) from the xorg-edgers ppa & also the latest mesa (9.1.1 or 9.2)

---

