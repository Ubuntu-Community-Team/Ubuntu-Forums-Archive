---
title: "Find the default library paths and default headers include paths"
date: 2024-01-22
forum: Ubuntu, Linux and OS Chat
---

### Post by luca-ub-1993 on 2024-01-22
[COLOR=#000000]I'm on an Ubuntu 22.04 system and I'm working with C language and libraries.[/COLOR]

[COLOR=#000000]I know ( from different books, included "The Linux Programming Interface" by Kerrisk ) that this algorithm is used when looking for runtime shared libraries locations ( I just omitted the preloaded libraries for the sake of simplicity ) :[/COLOR]

[COLOR=#000000]When RUNPATH field is specified (i.e. DT_RUNPATH is non-empty)[/COLOR]

[COLOR=#000000]1 ) LD_LIBRARY_PATH[/COLOR]
[COLOR=#000000]2 ) runpath (DT_RUNPATH field)[/COLOR]
[COLOR=#000000]3 ) ld.so.cache[/COLOR]
[COLOR=#000000]4 ) default library paths (/lib and /usr/lib)[/COLOR]

[COLOR=#000000]In the absence of RUNPATH (i.e. DT_RUNPATH is empty string)[/COLOR]

[COLOR=#000000]1 ) RPATH[/COLOR]
[COLOR=#000000]2 ) LD_LIBRARY_PATH[/COLOR]
[COLOR=#000000]3 ) ld.so.cache[/COLOR]
[COLOR=#000000]4 ) default library paths (/lib and /usr/lib)[/COLOR]

[COLOR=#000000]The problem is that most books say that generally speaking the default library paths are /lib and /usr/lib but they don't mention [/COLOR][B]HOW I CAN GET THE EXACT DEFAULT LIBRARY PATHS FOR MY SYSTEM. What command can I use on my Ubuntu 22.04 system ?

[B]What about the default headers include paths ? What command can I use the get them ?

And finally what is the specific algorithm used in my ubuntu system when dealing with "headers.h" vs <headers.h> ?[/B][/B]

---

### Post by slickymaster on 2024-01-22
Closed

Duplicate [here]("https://ubuntuforums.org/showthread.php?t=2494626")

---

