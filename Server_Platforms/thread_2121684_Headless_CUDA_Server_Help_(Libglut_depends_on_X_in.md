---
title: "Headless CUDA Server Help? (Libglut depends on X in apt)"
date: 2013-03-02
forum: Server Platforms
---

### Post by mattlach on 2013-03-02
Hey all,

I am trying to set up a headless CUDA rendering server, but trunning into some problems.

The Nvidia CUDA developer toolkit depends on libglut, but installing freeglut3, freeglut3dev and binutils-gold, apt is trying to install all of X and all of its dependencies.

I neither need nor want X on this system.

Can anyone please help me figure out a good way to install libglut without X?

This is on Ubuntu Server 12.10.

Thank you,
Matt

Edit:  It appears to be only Freeglut3-dev that is trying to pull in all of X.   Maybe I can do without the dev package...

---

### Post by tgalati4 on 2013-03-02
You only need the -dev package if you plan on doing any compiling of source code.  It's OK to install X on the server, just disable the startup script.  You (may) need the libraries on the system, but you don't have to run the xserver.  I'm not familiar with the CUDA development environment, so others will have to chime in as to what libraries are required and what is optional.

---

### Post by mattlach on 2013-03-02
> **tgalati4 said:**
> You only need the -dev package if you plan on doing any compiling of source code.  It's OK to install X on the server, just disable the startup script.  You (may) need the libraries on the system, but you don't have to run the xserver.  I'm not familiar with the CUDA development environment, so others will have to chime in as to what libraries are required and what is optional.

Thank you for the info!

Turns out I am going to have to downgrade to 12.04 LTS, as apparently the CUDA 5.0 Toolkit doesn't support the newer version of GCC found in 12.10 (4.7.2)

CUDA seems to be pretty finicky...

---

