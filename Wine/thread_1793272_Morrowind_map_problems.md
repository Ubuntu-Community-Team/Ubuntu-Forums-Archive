---
title: "Morrowind map problems"
date: 2011-06-29
forum: Wine
---

### Post by Tomba1110 on 2011-06-29
Hi
I installed Morrowind on Wine 1.2.2 in Ubuntu 10.04 (lucid). Everything is fine except the mini-map and local map are not working - they're just black. The global map works fine. Also, character potrait is black too. I've been searching about how to solve this and I only found these sites:

[http://bugs.winehq.org/show_bug.cgi?id=9892](http://bugs.winehq.org/show_bug.cgi?id=9892)
[http://bugs.winehq.org/show_bug.cgi?id=9775](http://bugs.winehq.org/show_bug.cgi?id=9775)

Someone said on the site that I have to apply patches from second link. Since I'm pretty new to Linux and I don't know how to apply patches and stuff like that, so can anyone please help me. Just keep it simple something like step-by-step explanation because I'm a Linux noob :)

---

### Post by arao on 2011-08-13
try this OffScreenRenderingMode=backbuffer.
it works for me everytime.

---

### Post by Tomba1110 on 2011-08-14
What do you mean? What exactly should I do?

---

### Post by arao on 2011-08-14
try this, hope it helps

---

### Post by arao on 2011-08-14
> **arao said:**
> try this, hope it helps

I mean, you should go to wine regedit, find in HKEY_CURRENT_USER the folder Direct3D, and edit it. look at this to understand 

[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

---

### Post by Tomba1110 on 2011-08-15
The only thing I got in Direct3D is VertexShaderMode with the value "hardware", I created OffScreenRenderingMode=backbuffer and it still doesn't work. Should I create the rest of the values?

---

### Post by arao on 2011-08-15
yeah, you shoul try.......as I said it always works for me. good luck with that.

---

### Post by arao on 2011-08-15
> **arao said:**
> yeah, you shoul try.......as I said it always works for me. good luck with that.

ah, and in wine config, you may turn off pixel shading.

---

### Post by Tomba1110 on 2011-08-15
I created all the values like in the attached picture above but it still makes no difference. What about these solutions I found:

[http://bugs.winehq.org/show_bug.cgi?id=9892](http://bugs.winehq.org/show_bug.cgi?id=9892)
[http://bugs.winehq.org/show_bug.cgi?id=9775](http://bugs.winehq.org/show_bug.cgi?id=9775)

I just don't know how to apply them

---

### Post by arao on 2011-08-16
well, you can also try playonlinux, just install it and then use wine import, when that is done, you may use wine advance configuration to change the registrykeys  for the ones on the pic.

---

