---
title: "running slower then it use to.."
date: 2015-12-18
forum: Virtualisation
---

### Post by simba4 on 2015-12-18
Hi there,

I am using VirtualBox v4.3.3.4   I use it to run a script that I wrote.

In the last two weeks, I started to notice that the script, 'sometimes' running slower then it use to.

I  say 'sometimes' because there are days that it doesn't slow at all, and  there are occasions that it starts slow, but later it get back to its  normal speed.

I suspect that something in the VirtualBox causing it.

BTW,  about three weeks ago my system complained that it run out of disk  space. Looking around I found huge amount of *.webm files accumulating in each of my active VB folders.

They seem not nececary so I deleted them,
Later (I had to recover my VM), I set each VM_Instance not to use them (Video Capture).

Is it possible that these "Video Capture" causing the sluggishness of my script?

James

---

### Post by MAFoElffen on 2015-12-23
I agree. Yes. Video capture uses a lot of resources. Especially not a good idea if it is filling your VM image to it's max limit... and if it grows to an unlimited size, it fills your host's disk.

Curiosity prompts me to ask if there is a reason you had video capture on by default?

---

