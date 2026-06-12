---
title: "Runtime Error 429"
date: 2011-05-17
forum: Wine
---

### Post by highonpop on 2011-05-17
I just installed Ubuntu 11.04 on my laptop, added wine.

I installed a program for work, Anthem Prospector. Its a program used by insurance agents to quote life health and dental insurance.

I installed the program with no problems. IT even put an icon on my desktop when I was done.

But when I try to run the program it gives the the "runtime error 429 ActiveX can't create object"

fix for this? patch? something?


Im a first time Linux user too btw

---

### Post by gsmanners on 2011-05-17
You might try:

```
winetricks ie6
```

see: [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

### Post by highonpop on 2011-05-18
what does that code mean? am i supposed to type that somewhere?

I got winetricks, i installed ie6 as well as the activex control pad, then rebooted my computer just in case.... still doesnt work. Still getting the '429' ActiveX error

---

### Post by dino99 on 2011-05-18
you need to know which exact dll this prog use, then add it with winetricks (might be something like d3dx9 or so) then run winecfg

---

### Post by highonpop on 2011-05-18
i don't guess there would be an easy way of finding out which .dll it uses?

I opened it on my work desktop and looked at the background processes, but it only said rundll.exe not the actual dll it was running....

---

### Post by highonpop on 2011-05-18
I opened up the program on my windows machine...

opened the CMD and did a tasklist/m and it gave a long list of .dll's being used by this program, none of which were d3dx9, or anything even similar...

---

### Post by gsmanners on 2011-05-18
Just run gnome-terminal with that command I gave you. That will save you the time and effort.

---

### Post by sampaguita on 2011-07-19
> **highonpop said:**
> what does that code mean? am i supposed to type that somewhere?

I got winetricks, i installed ie6 as well as the activex control pad, then rebooted my computer just in case.... still doesnt work. Still getting the '429' ActiveX error

Same problem still doesn't work Runtime Error 429

---

### Post by glenndrew on 2011-11-24
Hello,
i also faced this problem many times but  i fixed it, i also got some help from this article  [COLOR=Blue]**[error 429]("http://www.error429.com")**[/COLOR] , hope someone might get help from this article.

Runtime error 429: “ActiveX component can’t create object”
Here is a solution to this error:
    Reinstall Windows Script
    Repair Windows Script File Information in Registry
    Reregister Concerning File
    Reset Internet Explorer Settings
    Restore your Computer
    Repair System Files

---

