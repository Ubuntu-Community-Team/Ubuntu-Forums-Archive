---
title: "Think its a driver isue.. EQ2 login fail (change resolution)"
date: 2010-05-16
forum: Wine
---

### Post by Larsm1980 on 2010-05-16
Okey.. my  problem is this.
 
Ive installed Everquest2 on ubuntu 10.04 with wine 1.1.44.. Its runs  fine... install and everything. But when i get to the character select  and press login it fails. 
However if i while i am at the screen where i select my character open  my nvidia x server and select my running resolution (1680x1050 60hz) and  apply, 
and then switch back to the game i can log in and play.. 
any ideas? im guessing it has something to do with the 3d driver..  opengl or directx.
But cant find anything that can help.
If i look at the wine regedit i cant find any directxrenderer key?
btw. If i try to change resolution ingame, the game fails.

---

### Post by asdfoo on 2010-05-18
can you post the terminal output here?

If you want to modify the settings in the registry, you need to first create the Direct3D part and then the key for the value you are trying to edit.

Before you do any of that, which video card and driver do you have?  (type glxinfo at a terminal and look near the top of the output)

A recent video driver for nvidia should start with 195.x.x if you have a geforce 6 or better I think.

---

