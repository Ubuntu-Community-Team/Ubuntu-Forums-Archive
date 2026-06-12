---
title: "WoW in Wine"
date: 2009-11-08
forum: Wine
---

### Post by Vistro on 2009-11-08
I made this exact post over on the WoW forums, and 1 hour, didn't even get 2 views.

I am having a lot of problems running WoW on Ubuntu 9.10. On 9.04, (the installer, at least, never really got to play the game) ran just fine. That won't even run without tweaking it. 

I've managed to install the game (have not even bothered to upgrade to WotLK, will do that AFTER I can get to a logon screen). 

Here is what I know so far.  

* The Launcher simply won't run. The two times I got it to, I got an error message from WINE. So much for a Gold supported program. 
* On D3D (DirectX), I can skip the cinematics, but I get greeted with a frozen program. This also happens if I let it run it's course. However, the first time I let it run it's course, it gave me the TOS box, and the cursor worked fine, but nothing I did affected anything. The snow in the background was not moving. 
* On OpenGL, (running through the terminal, so I can see the WINE error message in the terminal), whether I skip the cinematics or let them run their course, I always get the same result: WoW closes, and I see: 

r300VertexProgUpdateParams:Params Exhausted 

* WoW runs what it wants to, graphics wise. Creating a config.wtf file doesn't seem to affect it at all, because when I set it to DirectX, or OpenGL, it's seemingly random which one it goes to. 
* WoW sometimes offers "Hardware has changed. Reload default settings?" Whether I pick yes or no, again, it's random whether it uses DirectX or OpenGL. 
* There are two RunOnce.wtf files, one of them is RunOnce_WLK.wtf. Since it first froze on the TOS, I tried setting the various TOS read stuff to 0 and 1, instead of -1. I also sometimes changed the movie and expansion movie values to 0 and -1, instead of 1. Pick a combination of file(s), value(s) that were changed, and the value they were changed to. It will either make my cursor a black box, or have no affect. When it does the former, no WoW windows, movies, or boxed show up. 
* I tried various WINE versions. AppDB says that it's certified in WINE 1.1.39. So I tried running that. All of what I tried above was done in 1.1.39. 
* EVERYONE is able to run WoW under these conditions. Why not me? 

It saddens me that Blizzard will not make a client for a platform used by over 30 million people.                    

So I've come to the Ubuntu forums. What do I do now?

---

### Post by bodyguard on 2009-11-09
heve u been there [http://ubuntuforums.org/showthread.php?t=579378]("http://ubuntuforums.org/showthread.php?t=579378")?

---

