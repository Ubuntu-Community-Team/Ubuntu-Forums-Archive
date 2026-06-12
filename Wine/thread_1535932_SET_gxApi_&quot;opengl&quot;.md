---
title: "SET gxApi &quot;opengl&quot;"
date: 2010-07-21
forum: Wine
---

### Post by daz1uk on 2010-07-21
I have seen many posts advising that SET gxApi "opengl" inserted in the config.wtf file for WoW can improve graphics performance. On my installation this just causes Wow to crash? Does anyone have any ideas 

I really need to improve my graphics speed, Wow works perfectly in Windows so I no it's not a hardware issue.

---

### Post by cogadh on 2010-07-21
Actually, it could be a hardware issue, in an indirect fashion. The video card drivers for Linux aren't necessarily the greatest, depending on the hardware you have. Provide some system specs and maybe we can confirm or eliminate that.

---

### Post by daz1uk on 2010-07-21
Hi,

Thanks for your response.

It's a Samsung R20plus laptop, Core2Duo, X1250 on board graphics with 256mb shared in bios.

---

### Post by cogadh on 2010-07-21
Well, ATI certainly does not have the greatest support in Linux (or OpenGL for that matter), but the fact that it is relying on shared memory could be a bigger issue. By default, I don't believe Ubuntu loads the kernel module necessary for shared memory to work fully. Check this post for details:
[http://ubuntuforums.org/showthread.php?p=9534907#post9534907](http://ubuntuforums.org/showthread.php?p=9534907#post9534907)

---

### Post by daz1uk on 2010-07-22
Cogadh,

Thanks for pointing that out you were right on that one, interestingly though now wow fails to start regardless of using OpenGL or not, you got any ideas?

---

