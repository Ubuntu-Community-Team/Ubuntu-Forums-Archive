---
title: "wine 1.3.1 ghost recon asus netbook"
date: 2010-08-21
forum: Wine
---

### Post by lessmemorelove on 2010-08-21
hi all. i have the latest wine and am running lucid. trying to run the original ghost recon and i get this message:


fixme:win:EnumDisplayDevicesW ((null),0,0x32f508,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x32f508,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x32f508,0x00000000), stub!
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  329
  Current serial number in output stream:  333


i have used winetricks to try gdi or opengl. i have turned shaders on and off. i have tried backbuffer. tried all the different windows versions. ghost recon works fine in wine 1.3.1 on my pc with the nvidia card so i am guessing this is an intel issue in my asus 1005peb. any thoughts?

---

### Post by NightwishFan on 2010-08-22
I find that Intel cards do not work well at all with Wine. Try enabling or disabling both Vertex/Pixel Shaders (if you only did pixel). Also, perhaps try an older version of wine, such as 1.2, or 1.0.

---

### Post by lessmemorelove on 2010-08-22
thanks. tried vertex, too. the weird thing is wine1.2 (1.1.31-0ubuntu3) worked in karmic on this machine but wine1.2 (1.1.42-0ubuntu4) does not in lucid. i have to use 1.0 in lucid. sometime after 1.1.31 there must be a problem.

---

