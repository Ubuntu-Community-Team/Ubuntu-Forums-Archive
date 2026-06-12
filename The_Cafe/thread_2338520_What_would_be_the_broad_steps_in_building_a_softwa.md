---
title: "What would be the broad steps in building a software layer between ubuntu and windows"
date: 2016-09-29
forum: The Cafe
---

### Post by deepakmp316 on 2016-09-29
[COLOR=#111111][FONT=Ubuntu]Hypothetically, if we were trying to build a bridge between two OSes (Ubuntu and Windows), how could we go about doing it? The effect is that, both OSes should be able to use installed softwares/programs i.e., install someone in one and you could already use it in another, yet retain the key features of respective OSes. Not talking about virtualization-something more native-where in, I could simply use the programs installed in my Win7 C drive directly from Ubuntu or vice-versa, as though they were natively installed.[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]

Most people say isn't really possible and I get that somewhat. But what if you could win a reward of USD 10 Mn? I mean, there has got to be some level of abstraction of windows from which we can connect to a similar deeper level of Ubuntu, and possibly set up a 50 or 100 GB dedicated partition just to serve as a bridge? We could use the drive to install stuff (rather than tradition C/home) or let the OSes use the space to store intermediary files? Or some sort of software layer or API between the two OSes.

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]Looking to some senior guys, with some strong understanding of softwares (particularly OSes, ubuntu, windows) to shed some clarity and share perspective? How could we build something like Ubuntu-Windows-bridge?[/FONT][/COLOR]

---

### Post by &amp;KyT$0P# on 2016-09-29
> **deepakmp316 said:**
> Most people say isn't really possible 
:-k
I'll just say "[WINE]("https://duckduckgo.com/Wine_%28software%29?ia=about")" and "Linux Subsystem for Windows 10", then leave this discussion to those who have used that type stuff for more than 1 hour total. :-\"

---

### Post by ian-weisser on 2016-09-29
> **deepakmp316 said:**
> [COLOR=#111111][FONT=Ubuntu]Most people say isn't really possible
It isn't really possible because an understanding of many Windows system calls isn't available to the public - that's intellectual property actively protected by Microsoft.
Were such an understanding available, WINE would have long ago duplicated near-complete Windows functionality for most applications...and few would be purchasing Windows anymore. 

[/FONT][/COLOR]> **deepakmp316 said:**
> [COLOR=#111111][FONT=Ubuntu]there has got to be some level of abstraction of windows from which we can connect to a similar deeper level of Ubuntu
Without the details of exactly how Windows functions, the closest level of abstraction is Wine (system level) and Virtualization (hardware level).Take your pick. 

[/FONT][/COLOR]> **deepakmp316 said:**
> [COLOR=#111111][FONT=Ubuntu]How could we build something like Ubuntu-Windows-bridge?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Such a bridge requires both parties to cooperate. Currently, one is not interested. [/FONT][/COLOR]

---

### Post by mastablasta on 2016-09-29
> **ian-weisser said:**
> 
[COLOR=#111111][FONT=Ubuntu]Such a bridge requires both parties to cooperate. Currently, one is not interested. [/FONT][/COLOR]

possible solutions:
1. buy MS and open the code.
2. win a landslide election and use a special urgent directive to confiscate the windows source code and open it
3. a few illegal ones.

---

