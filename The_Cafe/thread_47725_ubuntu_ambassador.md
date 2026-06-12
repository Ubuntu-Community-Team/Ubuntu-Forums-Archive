---
title: "ubuntu ambassador"
date: 2005-07-09
forum: The Cafe
---

### Post by nightfrost on 2005-07-09
This is my first post at the forums here, so I'm mainly posting this to break the ice - although I have a question as well. 

I've been wanting to register here for a while but I've been reluctant since ubuntu isn't my main distro. However, I think ubuntu is one of the best things that have happened the gnu/linux community lately, and I have done all I can to spread this wonderful distribution to people. I'm now considering to install Breezy on a separate partition in order to help with trouble shooting, etc. 

Anyway, I have one question: I am very impressed with ubuntu's xorg package. It's the only distro which allows me to suspend and resume without losing DRM (i810 driver, i915 module). I guess there are some CVS-patches at play here. Could anyone point me in the direction of any information on how that package was built? I can't find anything useful. Is it possible to download source packages from repositories (without having ubuntu installed)?

---

### Post by az on 2005-07-09
Good questions.

Firstly, visit packages.ubuntu.com and find the package you want.  At the bottom of the page you can see the changelog.

You can also see the list of files in the installed package.

You will find the .dsc .diff and .orig.tar.gz file for every package.

The .dsc is a description!

The .orig.tar.gz is the original upstream source
and the .diff is the added stuff (packageing information, pre and post install/remove scripts and changes made to the source by the package maintainer.  You can unpack them all yourself and apply the changes by hand yourself if you want to take a look.

---

### Post by nightfrost on 2005-07-10
Thanks a lot! That was precisely what I was looking for. However, I'm probably not knowledgeable enough to break out the relevant patches from that one big patch file. But I'll see what I can do :)

---

