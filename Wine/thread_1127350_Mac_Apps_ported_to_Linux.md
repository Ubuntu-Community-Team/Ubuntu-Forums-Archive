---
title: "Mac Apps ported to Linux"
date: 2009-04-16
forum: Wine
---

### Post by Kosimo on 2009-04-16
Wouldn't be easier to port a =nix program to Linux, than porting a windows program?

For example: If there is a game, like Warcraft III, that has a native windows (Direct3D) and Mac (OpenGl) versions, why try to put the Direct3D in wine and stuff, when we could use the Mac version that has been design to work native on OpenGl?

---

### Post by cogadh on 2009-04-16
Mac &#8800; Linux and there are no facilities like Wine that allow you to run Mac software on Linux. Besides, even though some games and apps have Mac versions, not all of them do. In fact, I would probably say the vast majority of them do not, so you would only have a very limited number of applications available when the idea with Wine is to have all applications available.

---

### Post by Kosimo on 2009-04-16
> **cogadh said:**
> Mac &#8800; Linux and there are no facilities like Wine that allow you to run Mac software on Linux. Besides, even though some games and apps have Mac versions, not all of them do. In fact, I would probably say the vast majority of them do not, so you would only have a very limited number of applications available when the idea with Wine is to have all applications available.


I know that Mac doesn't means linux. Not either windows.
I was just pointing, that in my opinion the distance between Windows and linux should be bigger than the distance between mac and linux, specially in terms of OpenGl apps.

---

### Post by masterkoppa on 2009-04-16
Usually games that have MacOS ports are the same thing except that they change the video rendering method. You could easly find out if it was possible to change the Rendering Method like in World of Warcraft where you can change from Direct3D to OpenGl and improve performance. You should check the app database for tips regarding this. 

Also mac and linux are way more similar than linux and mac but still miles away for easy compatability.

---

### Post by cogadh on 2009-04-16
> **Kosimo said:**
> I know that Mac doesn't means linux. Not either windows.
I was just pointing, that in my opinion the distance between Windows and linux should be bigger than the distance between mac and linux, specially in terms of OpenGl apps.
Whether or not the distance between the two is greater or smaller is really moot, since you can't make a Mac application work on Linux without a Mac compatibility layer (like Wine does for Windows apps) or access to the source code in order to modify it for Linux use. In the end, the amount of work required to accomplish the task would be nearly equal. Besides, my initial point still stands about the sheer number of applications available on Windows as compared to Mac. Why bother coming up with a way to port or use a handful of applications over from Mac when the vast majority of apps (and users) are on Windows? Getting the Windows version of the app running in Wine is already easier at this point.

In regards to games, with at least some of the Windows games that have been "ported" to Mac, they aren't really ported, they are just wrapped in a Wine-like layer called Cider (from Transgaming, the guys responsible for Cedega). Finding a way to run those on Linux would be a real waste of time, since you would essentially be doing the same thing as running a Windows game in Wine. Many of the games that are actually ported are already using OpenGL or have OpenGL available in the Windows version, so the fact that the Mac version is solely OpenGL is really meaningless, in terms of what is required to make it work on Linux.

---

### Post by Kosimo on 2009-04-16
> **cogadh said:**
> Whether or not the distance between the two is greater or smaller is really moot, since you can't make a Mac application work on Linux without a Mac compatibility layer (like Wine does for Windows apps) or access to the source code in order to modify it for Linux use. In the end, the amount of work required to accomplish the task would be nearly equal. Besides, my initial point still stands about the sheer number of applications available on Windows as compared to Mac. Why bother coming up with a way to port or use a handful of applications over from Mac when the vast majority of apps (and users) are on Windows? Getting the Windows version of the app running in Wine is already easier at this point.

In regards to games, with at least some of the Windows games that have been "ported" to Mac, they aren't really ported, they are just wrapped in a Wine-like layer called Cider (from Transgaming, the guys responsible for Cedega). Finding a way to run those on Linux would be a real waste of time, since you would essentially be doing the same thing as running a Windows game in Wine. Many of the games that are actually ported are already using OpenGL or have OpenGL available in the Windows version, so the fact that the Mac version is solely OpenGL is really meaningless, in terms of what is required to make it work on Linux.

This is the answer I was looking for.
Actually I had no clue about "cider" and how a game is ported to Mac. (There are no 100% native games for mac?) 
I agree that is much better to work on creating a compatibility layer for Windows Apps, as there are much more apps than in any other platform. The question I asked before was more focused on how "easier" would it be to port a Mac app to Linux.

Thank you for the answer

---

### Post by cogadh on 2009-04-17
Not all Mac games are ported using Cider, but [some are]("http://www.transgaming.com/products/cider/games/"). There are actually native Mac games, but most are ports of Windows games that were already using open standards like OpenGL while on Windows.

---

