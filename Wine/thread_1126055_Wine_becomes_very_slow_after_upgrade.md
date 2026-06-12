---
title: "Wine becomes very slow after upgrade"
date: 2009-04-15
forum: Wine
---

### Post by Hikayu on 2009-04-15
Hi! I never had to post a thread for about 8 months thanks to the current diversity of useful posts in this forum. This is SOME of the few I couldn't find:

  After upgrading wine 1.1.15 to 1.1.19, the speed taken to run ANY windows applications slows downs tremendously. And no : I did not make ANY major changes between the two wine versions (Except upgrading to Ubuntu 9.04 jaunty jackolope)

  I have an dll overide for msxml(native, builtin) (I can;t remember why)

  My default version for running applications is Windows XP




  Anyway, in THIS example I will attempt to open "winecfg" in the terminal. (I will mark comments with #)

```
hikayu@Hikayu:~$ winecfg
#Some long wait (about 20 seconds)
err:process:__wine_kernel_init boot event wait timed out #Winecfg opens
#winecfg closes
hikayu@Hikayu:~$
```

---

### Post by NightMKoder on 2009-04-15
[http://www.nabble.com/boot-timeout-problems,-e.g.-winecfg-td22075943.html](http://www.nabble.com/boot-timeout-problems,-e.g.-winecfg-td22075943.html)

Seems you got some bad mojo in your wine prefix. Assuming you don't have anything important installed, you can nuke the wine prefix. A poster suggests nuking the windows folder, but that may not work too well since you have an override.

---

### Post by Hikayu on 2009-04-16
I was able to lighten the speed XD, in other words : YEP, that worked. I"m a lil worried though. I deleted everything in my "~/.wine/drive_c/windows" folder. Will things still run nicely?

---

