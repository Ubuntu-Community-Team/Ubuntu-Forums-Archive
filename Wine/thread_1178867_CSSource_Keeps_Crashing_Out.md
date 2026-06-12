---
title: "CS:Source Keeps Crashing Out"
date: 2009-06-05
forum: Wine
---

### Post by beastrace91 on 2009-06-05
CSS keeps dumping on me after a few moments of game play... right now all my winecfg settings are at defaults. Here is the last bit outputted in terminal before the game dumps: ```
(D) C:\Program Files\Steam\steamapps\beastrace91\counter-strike source\hl2.exe
00000057 0
0000005e 0
00000040 0
0000003f 0
00000042 0
0000003a 15
0000003b 0
00000060 0
0000004e 15
00000067 15
0000002e 2
0000004b 0
0000003c 0
00000033 0
00000034 2
00000055 0 0 0x0e0bb423 in datacache (+0xb423) (0x00000002)
1 0x00000000 (0x00000000)
err:seh:setup_exception_record stack overflow 1244 bytes in thread 0055 eip 7bc3c52e esp 00240e54 stack 0x240000-0x241000-0x340000
```

Anyone have any idea if there is anything I can do to get this working?

~Jeff

---

### Post by asdfoo on 2009-06-05
video driver version? 180.44 or newer would be good.

---

### Post by beastrace91 on 2009-06-05
Do you think that could be the issue? I'll run and get the latest nVidia drivers now. ATM I am just using 180.11 provided by 8.10

~Jeff

---

### Post by beastrace91 on 2009-06-05
Just upgraded to the 180.60 driver and it is still crashing just the same. Any other ideas? Should I try the 185.xx driver?

~Jeff

---

### Post by fut21 on 2009-06-15
Look at this tread:
[http://ubuntuforums.org/showthread.php?t=1167746&highlight=counter+strike&page=2](http://ubuntuforums.org/showthread.php?t=1167746&highlight=counter+strike&page=2)

---

### Post by beastrace91 on 2009-06-15
Yea, I had already seen that one. My issue ended up being I had forgot to turn off in-game friends network.

~Jeff

---

