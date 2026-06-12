---
title: "Debugger crashing"
date: 2009-08-06
forum: Wine
---

### Post by Askar450 on 2009-08-06
I get this error message saying it could not find the symbol module, I can't find a fix for this.
0[1b3810]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nssutil3.dll") - Symbol NSGetModule not found
0[1b3810]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\ssl3.dll") - Symbol NSGetModule not found

Everytime I exit out of a game it says 
wine: Unhandled page fault on read access to 0x00000004 at address 0x7ceb3a38 (thread 002d), starting debugger...

Then it crashes...

Unhandled exception: page fault on read access to 0x00000004 in 32-bit code (0x7ceb3a38).

and a bunch of modules

Module    Address            Debug info    Name (154 modules)
PE      340000-  386000    Deferred        tier0
PE      390000-  3ea000    Deferred        vstdlib
PE      400000-  41a000    Deferred        left4dead
PE     5ba0000- 5bdc000    Deferred        gameoverlayrenderer

Anyone know why I'm getting this error? Its becoming a problem now cause the program that crashes, hangs and I can't open the file without going to System Monitor and end process if I don't the sound is stuck and I can't hear anything from the other games. The weird part is the only program not affected by this is Steam Client.

---

