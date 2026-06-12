---
title: "Elementary OS hot corners not working"
date: 2014-01-26
forum: Ubuntu/Debian BASED
---

### Post by bhatbhai on 2014-01-26
Hey all,

I've got an issue that I haven't had before. Seemingly out of the blue,  my hot corners no longer respond. Settings still shows that the hot  corners have actions to perform, but going to the hot corner does not  trigger the action. I haven't installed any new software recently, just  whatever updates via update manager.

Any ideas on how to resolve this?

---

### Post by ibjsb4 on 2014-01-26
Haven't tried hot-corners in a while, a search in synaptic shows only brightside.  So if I remember right, the package "xdot" triggered this.  Take a look and see if you have xdot installed, if so, reinstall.

---

### Post by bhatbhai on 2014-01-26
Did not have xdot installed. Installed it, logged out/in and still no hot corner love. 

Any other ideas? :/

---

### Post by slooksterpsv on 2014-01-26
Last time I ran into this issue, I had to disable the hot corners and set them up again. That worked for me. Do you have a secondary monitor or that attached?

---

### Post by bhatbhai on 2014-01-26
Realized I also didn't have brightside installed. Installed that, tried again, nothing.

> **slooksterpsv said:**
> Last time I ran into this issue, I had to disable the hot corners and set them up again. That worked for me. Do you have a secondary monitor or that attached?

Oh man, got my hopes up with such a simple but common sense solution. Tried it, still nothing. No secondary monitor attached.

---

### Post by slooksterpsv on 2014-01-27
Try creating a new user and see if it works under that, it could be a botched configuration file

---

### Post by bhatbhai on 2014-02-01
> **slooksterpsv said:**
> Try creating a new user and see if it works under that, it could be a botched configuration file

Tried that out, still no luck with the hot corners. Any other ideas? Or will I have to reinstall the OS if I want my hot corners working again?

---

### Post by slooksterpsv on 2014-02-03
I'm all out of ideas, you can submit a bug report to elementary and see if they could help.

---

### Post by Stinger on 2014-02-04
The desktop effects rely on working 3D graphics, maybe thats your problem ?
Try ```
glxinfo | grep render
```  in a terminal and see what output you get. Mine is > direct rendering: Yes
OpenGL renderer string: Gallium 0.4 on AMD RV730
    GL_EXT_vertex_array_bgra, GL_NV_conditional_render,

---

### Post by caffeinatedev on 2014-02-15
I hope for the day when we have our own forum :-/

Edit: welp, saw the link above my post and face palmed. Bookmarked the elementary forums. :B

---

