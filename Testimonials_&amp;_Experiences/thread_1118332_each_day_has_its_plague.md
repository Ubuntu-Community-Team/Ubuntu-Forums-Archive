---
title: "each day has its plague"
date: 2009-04-06
forum: Testimonials &amp; Experiences
---

### Post by armandh on 2009-04-06
I find that when I mess with the xconfig it dumps the 3D drivers

I know what the problem is 
an old monitor that does not communicate to the os
there is no easy button on this and when I tried a recommended CL fix... compiz quit. well I needed to replace 8.04 with 8.10 anyway. and I put a good monitor on it.

I took the problem monitor to an old 866 P-III that runs 8.10 fine, 
putzing around I screwed compiz again. this problem needs an easy button. I think I'll put 9.04 on this one. 

found this sort of easy buttons
I re installed 3D driver and restarted. set glitz to extra. 
re checked the compiz config manager's options and it works

---

### Post by Thelasko on 2009-04-07
You need to add a virtual line under the "Display" subsection.  [Here are some instructions.]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2")Don't touch anything outside of the "Display" subsection.  Virtual screen sizes larger than 2048 by 2048 kills graphics acceleration on some cards.

I agree, this problem needs an easier solution.

---

