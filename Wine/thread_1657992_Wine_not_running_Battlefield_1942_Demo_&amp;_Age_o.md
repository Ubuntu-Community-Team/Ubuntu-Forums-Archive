---
title: "Wine not running Battlefield 1942 Demo &amp; Age of Empires II"
date: 2011-01-01
forum: Wine
---

### Post by layers on 2011-01-01
OK, here is the first problem: When I install Battlefield 1942 Demo, and run the executable, all it does is that the little circle on the mouse appears for a few seconds and then nothing. Is there anything specific I need to do to run the game at all?

It is Wine 1.2, btw.

Secondly, When trying to play age of Empires 2, the fonts in the menu are all black, so it is very hard to see. Anyways, if you really try hard, you could go into the start game screen, at which point you tell it to start and it freezes. I found that if I open winecfg in the background and then close it, the game unfreezes and opens up the game with the map and so forth. If anyone know a way to fix all these little issues, please help.

My main beef with AoE2 is that in the Multiplayer menu, there is ONLY TCP/IP connection listed - no LAN. What gives?

Thanks a lot in advance.

---

### Post by cogadh on 2011-01-02
Have you checked Wine's [Application Database]("http://appdb.winehq.org/") to see first if either game actually works in Wine and if so, what extra steps you might need to take to get them running their best? What kind of error output do you get from Wine when you run the games from the terminal? What do you have for a video card and have you installed the restricted driver for it (if it has one)? 

Not sure on the AoE LAN thing, don't know enough about that game in particular to offer any advice on that front.

---

### Post by layers on 2011-01-02
> **cogadh said:**
> Have you checked Wine's [Application Database]("http://appdb.winehq.org/") to see first if either game actually works in Wine and if so, what extra steps you might need to take to get them running their best? What kind of error output do you get from Wine when you run the games from the terminal? What do you have for a video card and have you installed the restricted driver for it (if it has one)? 

Not sure on the AoE LAN thing, don't know enough about that game in particular to offer any advice on that front.

Well, yes, I have:

Both games do run in wine:
[Battlefield 1942 Demo]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=6669")
-according to the above, "everything works". On my machine, there is no error, no nothing.

[Age of Empires 2 Gold Expansion]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=147")
-according to this, the font is a known problem and there might be something to be done to get multiplayer *working*, I need to do something extra: > To get multiplayer working, place the DLLs in this archive in Wine's windows/system32 directory. Then, start winecfg and add dll overrides (native, builtin) for the following DLLs: dplayx, dpnet, dpnhpast and dpwsockx. It may work, or not.  However, me not think so this is the problem (plus, they skip steps which only makes the level of the language even higher).

I am not running anything from terminal, just through the Windows drive folder explorer. Should I be?

There are no restricted drivers for the Mobile Intel 945GM Express. Everything used to run under Windows XP.

---

### Post by cogadh on 2011-01-02
Actually, that's only according to one test result. If you check the other results, the game does not consistently "just work", but it appears it should work better than what you are seeing. Running the game from the terminal might tell us what is happening in this case.

Overriding DLLs is simply a part of using Wine. Sometimes Wine's implementation of certain DLL functions is not complete and the only way to get around it is to use actual Windows Dlls in place of the Wine ones. If it doesn't work, you can simply undo the override in winecfg to restore Wine's DLLs fully.

Technically, you should always run Wine from the terminal, at least until you get your application running its best. The only way to get any error output from Wine is to use the terminal and quite often that error output can explain precisely what is causing a problem, which will lead to a very clear solution, or at least an explanation that might tell you to stop trying.

You can't use how things ran on Windows as a comparison. Linux and Wine are not Windows. Hardware drivers are fundamentally different in most cases on Linux and since Wine is "translating" the Windows DirectX calls into OpenGL calls that can be understood by the Linux drivers, that can be an important factor in a game's performance. That being said, the Linux Intel drivers are not the greatest, even worse than the Intel drivers in Windows can be. I wouldn't expect your game performance to be all that great, even if we can get the games to work.

---

### Post by layers on 2011-01-02
This is what I get from Battlefield 1942:

> ibo@ibo-laptop:~/.wine/drive_c/Program Files/EA GAMES/Battlefield 1942 Multiplayer Demo$ wine BF1942Demo.exe
err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\Program Files\\EA GAMES\\Battlefield 1942 Multiplayer Demo\\BF1942Demo.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\EA GAMES\\Battlefield 1942 Multiplayer Demo\\BF1942Demo.exe" failed, status c0000135


Now, how do I find that and where do i put it?

---

### Post by cogadh on 2011-01-03
Ah, that one's easy. The game is looking for a component of MS Visual C++ runtime. You just need to install the runtime using [winetricks]("http://wiki.winehq.org/winetricks") (install the vcrun and vcrunsp6 packages).

---

### Post by layers on 2011-01-04
alright, after installing the packages it worked, thanks.

---

