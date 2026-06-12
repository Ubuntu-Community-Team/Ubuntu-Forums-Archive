---
title: "Direct3D 9 Support Released For Linux Via Gallium3D, Running Games"
date: 2013-07-17
forum: Ubuntu, Linux and OS Chat
---

### Post by synaptix on 2013-07-17
Totally sweet, especially for us open source driver users.

[http://www.phoronix.com/scan.php?page=news_item&px=MTQxMjk](http://www.phoronix.com/scan.php?page=news_item&px=MTQxMjk)

> Linux desktop systems can now have working support for Microsoft's  Direct3D 9 API via a new Gallium3D state tracker. Unlike the earlier  Direct3D 10/11 state tracker for Gallium3D on Linux, this new code  actually can run D3D9 games and at better performance than what's  offered by Wine. 

Back in 2010, [Direct3D 10/11 was natively implemented for Linux]("http://www.phoronix.com/vr.php?view=15292")  in the form of a Gallium3D state tracker. While Gallium3D is most often  associated with OpenGL, its API agnostic and handles OpenGL ES, OpenVG,  and even OpenCL for compute support, among other interfaces. Gallium3D  can work just as well with Direct3D, but there has traditionally been  not much developer interest in such a state tracker. This isn't to be  confused with a translation layer whereby Direct3D commands are mapped  into OpenGL. 

The Direct3D 10/11 state tracker excitement was ultimately shortlived as [the upstream Wine development community wasn't interested in adding support]("http://www.phoronix.com/scan.php?page=news_item&px=ODYyNw")  for it since it's a Linux-only solution and at that it's limited to  those using Gallium3D, which is basically the open-source Radeon and  Nouveau (NVIDIA) users. This D3D 10/11 state tracker was [ultimately removed from Mesa]("http://www.phoronix.com/scan.php?page=news_item&px=MTMyNDU") since it wasn't being used and [the code was suffering bit-rot]("http://www.phoronix.com/scan.php?page=news_item&px=MTE3ODE").

---

### Post by mastablasta on 2013-07-17
awesome. and new 3.11 kernel (linux for workgroups -->LOL) got improved support from AMD. They've added plenty new features into opensource driver.

but anyway. how does this actually help us if it's not in wine (that runs most windows games)?

---

