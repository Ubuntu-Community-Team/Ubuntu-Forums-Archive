---
title: "specific use for Wine"
date: 2009-12-11
forum: Wine
---

### Post by TheShabz on 2009-12-11
hey all,

currently im dualbooting Jaunty with XP. rather than using Wine to install windows software here can I merely mount my windows partition and use Wine to run software using the dependencies already installed on my windows partition? For example, using software already installed in windows along with the .NET environment thats already in windows. 

i find that many of the issues i experience with Wine is the installation of programs and dependencies, not actually running them. So I figure why not install using Windows and just use Wine to run it?

thoughts?

---

### Post by SuperSonic4 on 2009-12-11
Because wine compiles to ~/.wine/c_drive or similar and doesn't look for windows deps. Generally it doesnt have to because exe files are often self-contained.

Also I don't think exe files allow you to compile in order to change the library path

---

### Post by TheShabz on 2009-12-11
well i tried it out and am getting the same error that i do normally, the software is actually trying to run. i tried AIM from my windows partition and it partially loaded, but its still using the same .NET that i installed using Wine and thats causing my issues. theres no way to just give Wine a pointer to my .NET folder?

---

