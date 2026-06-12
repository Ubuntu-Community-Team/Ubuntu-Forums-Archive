---
title: "Qemu opengl"
date: 2007-04-06
forum: The Cafe
---

### Post by dlai on 2007-04-06
Hi everybody,

I guess I am not the only one listening to linux action show once in a while, though I am more fond of LUGRadio and FLOSS Weekly. Anyway last show they explained about the possibility of enabling opengl in virtualized environments like vmware, qemu and xen. The project is called vmgl.... You can find a link to it on linux action shows homepage. After doing some research I found a patch for qemu which enables opengl in qemu. I packaged qemu-opengl with checkinstall... so I'm not sure how well it works on other computers. I installed qemu from the repositories first and then this one on top. Hope you like it. [qemu-opengl]("http://imi.aau.dk/~jfur05/linux/qemu-opengl_20070406-1_i386.deb")

---

### Post by GeneralZod on 2007-04-06
Neat! How well did it work for you? What did you test it with? Anything taxing like Beryl, etc ... ?

---

### Post by SishGupta on 2007-04-06
Thanks for posting this!

Can we get some more info about this?
Can i have the source? Where is the official website?

Does it work with XP? i want to use joost!

---

### Post by reacocard on 2007-04-06
Point me at the source and I'll try to build a proper deb. Checkinstall is handy, but the debs it creates really aren't suitable for distribution.

---

### Post by dlai on 2007-04-06
so I've been surfing around tryíng to find a livecd which could let me test this, but then I remembered the problems with kororaa... and sort of gave up... the source code is here I could only make it build with
```
./configure --target-list=i386-linux-user,i386-softmmu,x86_64-softmmu
```

you should be able to run the gl acceleration by adding -enable-gl when executing        

[here]("http://imi.aau.dk/~jfur05/linux/qemu-opengl.zip")

---

### Post by dlai on 2007-04-06
[Link to vmgl]("http://www.cs.toronto.edu/%7Eandreslc/xen-gl/")

[The forum thread discussing the patch for qemu]("http://qemu-forum.ipi.fi/viewtopic.php?p=9867#9867")

---

### Post by bash on 2007-04-06
Anyone willing to do such a package for virtualbox?

---

### Post by reacocard on 2007-04-06
ARGHH!!!! Qemu, why must you be so hard to build! It refuses to be coaxed into a deb properly (it install to my harddrive instead), and what did get compiled doesn't work. So, no deb, I'm afraid.

---

### Post by dlai on 2007-04-09
Anyway did anyone try out the source code, haven't really had time yet. But it would be nice if anybody had anything to show off.

---

### Post by bastiegast on 2007-04-09
And will this work with Direct3d as well?

---

### Post by dlai on 2007-04-11
Not according to the vmgl website

---

