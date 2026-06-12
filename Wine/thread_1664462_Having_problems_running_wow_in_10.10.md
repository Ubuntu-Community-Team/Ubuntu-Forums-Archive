---
title: "Having problems running wow in 10.10"
date: 2011-01-11
forum: Wine
---

### Post by Lunytoast on 2011-01-11
Alright, i'm brand new to ubuntu, just started on it two days ago and i'm having a lot of trouble getting wow to work under wine(version is 1.2.1), so far i've read through a guide and have gotten it to install and gotten the launcher to patch up to the latest version of wow, i've also gotten direct rendering in ubuntu via the terminal, but i'm having problems actually getting the game to run.

So far when i hit "play" on the launcher it opens up wow, goes through the cataclysm cinematic normally but when the cinematic ends (prematurely or otherwise) an error pops up before it has time to get to the login screen, the error is as follows:

ERROR #132 (0x85100084) Fatal Exception
Program:    Z:\home\jordan\Desktop\World of Warcraft\Wow.exe
Exception:    0xC0000005 (ACCESS_VIOLATION) at 0073:B76ED08A

The instruction at "0xB76ED08A" referenced memory at "0x0000000C".
The memory could not be "read".

any idea how i could fix this?

---

### Post by cwwilson721 on 2011-01-11
[LIST]
[*]What videocard/chip do you have?
[*]Have you tried wine 1.3? It REALLY fixes MANY issues
[*]Are you running in D3D or opengl? (opengl preferred)
[*]Do you have Compiz disabled?
[*]Do you have the latest proprietary video drivers installed?
[*]What version of Windows is wine using? 
[/LIST]If you don't know the answers, or need help with how to figure them out, SEARCH THIS FORUM

---

