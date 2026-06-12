---
title: "GProxy++ is a disconnect protection tool for use with Warcraft 3"
date: 2010-07-20
forum: Wine
---

### Post by miodragsupportpub on 2010-07-20
Does  anyone know how to solve this problem :popcorn:
Can do work GProxy ++ tool with wine?

"GProxy++ is a disconnect protection tool for use with Warcraft 3 when  connecting
 to specially configured GHost++ servers. It allows the game  to recover from a 
temporary internet disruption which would normally  cause a disconnect."


```

miodrag@office:~$ wine /home/miodrag/.wine/drive_c/Program\ Files/Warcraft\ III/GPRoxy/gproxy.exe
[CONFIG] loading file [gproxy.cfg]
[GPROXY] starting up
[GPROXY] starting winsock
[GPROXY] setting process priority to "above normal"

  Welcome to GProxy++.
  Server: eurobattle.net
  Username: biosmm
  Channel: playdota.eu

LINES value must be >= 2 and <= 29764: got -1
initscr(): Unable to create SP
miodrag@office:~$ 


```

---

### Post by asdfoo on 2010-07-22
> **miodragsupportpub said:**
> Does  anyone know how to solve this problem :popcorn:
Can do work GProxy ++ tool with wine?

"GProxy++ is a disconnect protection tool for use with Warcraft 3 when  connecting
 to specially configured GHost++ servers. It allows the game  to recover from a 
temporary internet disruption which would normally  cause a disconnect."


```

miodrag@office:~$ wine /home/miodrag/.wine/drive_c/Program\ Files/Warcraft\ III/GPRoxy/gproxy.exe
[CONFIG] loading file [gproxy.cfg]
[GPROXY] starting up
[GPROXY] starting winsock
[GPROXY] setting process priority to "above normal"

  Welcome to GProxy++.
  Server: eurobattle.net
  Username: biosmm
  Channel: playdota.eu

LINES value must be >= 2 and <= 29764: got -1
initscr(): Unable to create SP
miodrag@office:~$ 


```

a) make sure you have wine-1.2, open a terminal and type 'wine --version'

b) cd to the install directory and then start it.

---

