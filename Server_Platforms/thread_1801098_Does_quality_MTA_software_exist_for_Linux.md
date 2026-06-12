---
title: "Does quality MTA software exist for Linux?"
date: 2011-07-09
forum: Server Platforms
---

### Post by steptotheedge on 2011-07-09
I currently run a server. The web server (Abyss X1) runs on Linux, and the MTA server (MERCURY) runs in a virtualized Windows environment, within Linux.

I am soon going to be building a dedicated server, and at the moment it looks like it will be a Windows-based server, as I can't find MTA software for Linux with the feature I require.

I need MTA software that can show me network verbose output in real time, as such does MERCURY in the following screen shot:

[http://i55.tinypic.com/1254a6q.png](http://i55.tinypic.com/1254a6q.png)

Does anyone know if such MTA software for Linux exist?

MERCURY does not work correctly under WINE, so the WINE method is not an option.

---

### Post by volkswagner on 2011-07-09
Would increasing the verbosity of Postfix give you the info you want?

[http://www.postfix.org/DEBUG_README.html#verbose](http://www.postfix.org/DEBUG_README.html#verbose)

---

