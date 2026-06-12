---
title: "Ubuntu Studio 13.04 randomly slowing to a crawl until reboot"
date: 2013-05-17
forum: Ubuntu Studio
---

### Post by glongshadow on 2013-05-17
Hi, first off let me just explain that while I'm competent with a computer and happy on the command line (as a programmer, I should be!), this is my first proper dive into Ubuntu.

I recently built a new machine, and have installed Ubuntu Studio 13.04, which on the whole I am extremely happy with, barring a few rather major issues.


[LIST=1]
[*]most problematically, the machine is randomly slowing to a complete crawl, with the mouse appearing to refresh at about 2Hz, sound stutters like a stuck cd, and the keyboard becomes extremely laggy. The only cure is a full reboot (logging out and back in has no effect, and the problems continue on the login screen). I have not been able to find any specific cause for this, and after 3 days of searching, have not yet found a solution, or more than one other person reporting a similar issue.
[*]On boot, I get a message on my monitor saying 'Mode not supported', which after some time disappears and allows a normal boot. I think this may be related to the fact that in the display settings the Refresh rate is set at 0.0 with no way to change it (xrandr made no difference either). Also related I think is what looks like a test screen on shutdown, which remains until I manually power down.
[/LIST]

I'm guessing it's very possible that all the above problems are inter-related, and I very much hope that a fix can be found, as it's driving me to distraction. 

I have a graphical hardware monitor installed, and can see that temperatures and loads are well within limits - averaging 34 - 38C, 5% load on the processor. 

Basic specs are below:

AMD FX 6100 processor
Gigabyte GA-78LMT-USB3 mobo
Radeon HD6450
Patriot 'Viper 3 Black Mamba' RAM (8GB)

If anyone has any ideas what could be causing the slowdowns and the graphical problems, please guide me through fixing it as I may otherwise end up returning to the dark side of Windows (shudder).

If any more information is necessary, I will happily provide it  in the hope of a faster solution!

---

### Post by zequence on 2013-05-20
Have you been monitorin RAM usage during your sessions? Kind of sounds like there could be a memory leak with some application, and that you end up with max RAM usage. When that happens, the SWAP space is used for normal RAM usage, and that makes things extremely slow.
But, I don't get the thing witht he mouse getting slow. So, perhaps it is a problem with your graphic card after all?

---

