---
title: "Flickering on SciTE"
date: 2014-02-06
forum: Ubuntu Development Version
---

### Post by Sworddragon on 2014-02-06
I have already created a bug report some time ago ([https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1260236](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1260236)) but as this problem gets now critical for me I'm looking here for help. After libgtk-3-0 got upgraded from version 3.8.x to version 3.10.x SciTE began to flicker on scrolling. But if I'm using the same version from upstream all is working fine. As I'm developing a lot it gets a big problem and for now I have to use the upstream version as a workaround.

Can somebody reproduce the problem too and has any idea what could cause it?

---

### Post by ventrical on 2014-02-06
Yes .. I reproduced the problem.  In the left hand column it is black and white and has a flickerty while scrolling a large .py file.

Also .. Me too'ed it! :)

---

### Post by ventrical on 2014-02-06
> **Sworddragon said:**
> 

Can somebody reproduce the problem too and has any idea what could cause it?

Perhaps a graphical aid in the GUI to help with a quick diff?

---

### Post by Sworddragon on 2014-02-07
I'm not sure if I understand you correctly. Do you mean that this could be a feature of SciTE that is just defect?

Currently the flickering on scrolling really hurts in the eyes. But I have now just compiled SciTE 3.3.9 on x86_64 myself (as the binaries provided by upstream are 32 bit only) and it works fine.

---

### Post by ventrical on 2014-02-07
> **Sworddragon said:**
> I'm not sure if I understand you correctly. Do you mean that this could be a feature of SciTE that is just defect?

Currently the flickering on scrolling really hurts in the eyes. But I have now just compiled SciTE 3.3.9 on x86_64 myself (as the binaries provided by upstream are 32 bit only) and it works fine.


Yes .. that is what I meant .. but apparently it looks not to be the case since your method has solved the problem. In the older days of programming  using older machines there would be this type of raster (flickerty) on the screen when programming in machine language. It was a type of  'effect' that one just got used to that distinguished the terminal from the GUI.

Regards..

---

### Post by wildflower1975 on 2014-08-05
A manual recompile to 3.4.4 fixed it for me too :)

---

### Post by Sworddragon on 2014-08-05
The issue should also be fixed since the Ubuntu package version 3.4.2-1.

---

