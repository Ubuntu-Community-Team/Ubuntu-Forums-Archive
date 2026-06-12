---
title: "Nvidia prop. drivers with studio 9.10 rt kernel?"
date: 2009-12-29
forum: Ubuntu Studio
---

### Post by barisurum on 2009-12-29
I consider switching to nvidia for my next gpu upgrade, maybe a gt2xx. Do they work well with the latest rt kernel?

---

### Post by barisurum on 2009-12-30
Bump No.1

---

### Post by AutoStatic on 2009-12-30
It's unsupported: [http://packages.ubuntu.com/karmic/nvidia-glx-185](http://packages.ubuntu.com/karmic/nvidia-glx-185)
But you could always try installing the drivers from the nvidia site, you will need the 190.xx drivers.

---

### Post by barisurum on 2009-12-30
Thanks for the info, but I wonder if the drivers (190 drivers in this case) work with rt kernel or not. 

And bump No.2 by the way :D

---

### Post by barisurum on 2009-12-31
Sorry but, Bump No.3

---

### Post by sgx on 2009-12-31
> **barisurum said:**
> Sorry but, Bump No.3
Hi, as a rule, I would get the best nvidia card that google searches reveal works in linux. Then try various distros/window-managers/kernels,
until you find a combination that works, and that you like. You may find that using 4 gig of ram, and a nice graphics card make an RT kernel less than mandatory in the short run. I found that having only one kernel installed helped when using nvidia 3D drivers. 

To make things easier, you might read up on restoring a working xorg.conf with a vi or nano style text editor from a root commandline. That insures that if things go blank during testing, you will still be the boss!

You can find examples of working commands, and edit them in to your
command history, for easy retreaving when/if needed.
Cheers

---

