---
title: "Cannot compile liballegro4.2"
date: 2007-04-22
forum: Repositories &amp; Backports
---

### Post by salsafyren on 2007-04-22
Hello,

Don't whether it is the right forum.

I want to compile liballegro4.2 which is a dependency for fakenes.

Reason: I want to build using apbuild from autopackage to make it work on distros with older glibc.

I am on edgy now. When I compile liballegro4.2, I get these errors:

/home/cs/.local/bin/apgcc -s -Wl,--export-dynamic  -o setup/setup obj/unix/setup.o -Llib/unix -lalleg-4.2.0 -lalleg_unsharable -lm
lib/unix/liballeg-4.2.0.so: undefined reference to `XRenderQueryExtension'
lib/unix/liballeg-4.2.0.so: undefined reference to `XRenderFreePicture'
lib/unix/liballeg-4.2.0.so: undefined reference to `XRenderFindStandardFormat'
lib/unix/liballeg-4.2.0.so: undefined reference to `XRenderCreateAnimCursor'
lib/unix/liballeg-4.2.0.so: undefined reference to `XRenderQueryVersion'
lib/unix/liballeg-4.2.0.so: undefined reference to `XRenderCreatePicture'
lib/unix/liballeg-4.2.0.so: undefined reference to `XRenderCreateCursor'
collect2: ld returned 1 exit status
make: *** [setup/setup] Error 1

I have run apt-get build-dep liballegro4.2.

What am I missing?

---

