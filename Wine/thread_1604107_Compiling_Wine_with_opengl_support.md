---
title: "Compiling Wine with opengl support"
date: 2010-10-23
forum: Wine
---

### Post by Peter7K on 2010-10-23
Hi all.  After upgrading to Maverick 10.10, and additionally using Nvidia beta drivers, it appears that my wine will not compile with opengl.  I'm assuming it's a library issue, and I have this error in my config.log:

wine libGL.dylib:/System/Library/Frameworks/OpenGL.framework/Versions/A/Libraries/libGL.dylib: No such file or directory

I've done the apt-get build-dep wine and it installs the mesa libs (which I'm told are for the opengl).  Other people seem to have similar conflicts with nvidia on other systems, but their fixes haven't worked for me.  

I'm using the ubuntu-wine-maverick ppa.  I have these relevant dev packages installed:

mesa-common-dev libgl1-mesa-dev libglu1-mesa-dev
All version 7.9~git20100924

Can someone help me resolve this please?  Thanks.

---

### Post by Peter7K on 2010-10-26
I've tried compiling with and without the affected libraries, they both give the same results (shocker).  Anyone have any input on this?  I'm getting rather frustrated. :(

---

### Post by Peter7K on 2010-11-02
Solved via updating/reinstalling Nvidia drivers.  Cheers.

---

