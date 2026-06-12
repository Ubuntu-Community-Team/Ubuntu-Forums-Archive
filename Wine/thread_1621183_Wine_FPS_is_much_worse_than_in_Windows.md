---
title: "Wine FPS is much worse than in Windows"
date: 2010-11-14
forum: Wine
---

### Post by l4nd0fc0nfu510n on 2010-11-14
I'm running Ubuntu 10.10 x64. On my Windows drive, I can run Team Fortress 2 completely maxed out and still get a steady 60 FPS.

On my Ubuntu installation, using the latest version of Wine, even if I turn down most of the settings to about Medium, I still only get around 10 FPS. There must be something wrong, right?

What can I do to fix this? I don't have Compiz installed. I've also installed DirectX properly on Wine, and I believe I get around 10,000 FPS using glxgears, so I'm pretty sure my drivers and stuff are all installed right.

Thanks.

---

### Post by Finalfantasykid on 2010-11-14
While some games might work quite well with wine, the fact is, most will probably work much slower.  Since everything has to go through an extra layer, the programs could potentially run half as fast as native programs.  If the game is DirectX, then there are definitely going to be some performance issues.

I havn't used Wine much, so maybe someone else can help you get better performance.  I have read that switching the game to use OpenGL instead of DirectX will improve performance, although I am not sure where this would be done.

---

### Post by alaukikyo on 2010-11-14
Everyone has compiz installed in the default install only ccsm(the setting manager is not installed)  
just alt +f2 before running the game and paste"metacity --replace &"(without the ") then when you have finished the game you could switch back to compiz using "compiz --replace")without ")

---

### Post by Tweak42 on 2010-11-15
FYI: for the gui version, search the ubuntu software center for "compiz fusion icon". It should add a launcher in Systems Tools menu.  Use icon applet to switch between compiz and metacity window managers.

---

### Post by cwwilson721 on 2010-11-16
TF2 is a Direct3D only game, so it will NOT run as fast in Linux/wine as in Windows. wine uses opengl, so...

And wine is NOT 'another layer' or an 'emulator'. wine just provides the API hooks for SOME windows programs to use so it can run on a Linux system (i.e., dll's, a 'registry', etc.) However, IT DOES NOT REPLACE WINDOWS! While they have made great strides in allowing a number of Windows programs to even run (which is a miracle in itself), there are a vast number that will not, and for the foreseeable futurw, never will, run on Linux.

But still, DISABLE COMPIZ (I use compiz-fusion-icon, I think it has changed names to fusion-icon)

Do a Google search of "tf2 d3d wine fps" to see if there's anything useful for you. (Maybe install D3D? Never done that myself, but...)

---

