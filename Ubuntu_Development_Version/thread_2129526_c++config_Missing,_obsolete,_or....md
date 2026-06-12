---
title: "c++config: Missing, obsolete, or...?"
date: 2013-03-26
forum: Ubuntu Development Version
---

### Post by Sslaxx on 2013-03-26
Attempting to compile the AGS Engine from source, I've started to get this happening:

>  make --directory=Engine
make: Entering directory `/home/stuart/CVS/AdventureGameStudio/Engine'
CFLAGS = -O2 -pie -fpie -g -fsigned-char -Wfatal-errors -DNDEBUG -DAGS_RUNTIME_PATCH_ALLEGRO -DAGS_HAS_CD_AUDIO -DAGS_CASE_SENSITIVE_FILESYSTEM -DALLEGRO_STATICLINK -DLINUX_VERSION -DDISABLE_MPEG_AUDIO -DBUILTIN_PLUGINS -DRTLD_NEXT -I/usr/include/freetype2 -I../Engine -I../Common -I../Common/libinclude -I../Plugins 

CXXFLAGS = -fno-rtti -Wno-write-strings -fpermissive -O2 -pie -fpie -g -fsigned-char -Wfatal-errors -DNDEBUG -DAGS_RUNTIME_PATCH_ALLEGRO -DAGS_HAS_CD_AUDIO -DAGS_CASE_SENSITIVE_FILESYSTEM -DALLEGRO_STATICLINK -DLINUX_VERSION -DDISABLE_MPEG_AUDIO -DBUILTIN_PLUGINS -DRTLD_NEXT -I/usr/include/freetype2 -I../Engine -I../Common -I../Common/libinclude -I../Plugins 

LDFLAGS = -Wl,--as-needed 

LIBS = -rdynamic -L/usr/lib/i386-linux-gnu -lalleg -laldmb -ldumb -Wl,-Bdynamic -ltheora -logg -lvorbis -lvorbisfile -lfreetype -logg -ldl -lpthread -lm -lc -lstdc++ 

**make: *** No rule to make target `/usr/include/c++/4.7/i686-linux-gnu/bits/c++config.h', needed by `libsrc/hq2x/hq2x3x.o'. Stop.**
make: Leaving directory `/home/stuart/CVS/AdventureGameStudio/Engine'
stuart@sslaxxworks:~/CVS/AdventureGameStudio$ make --directory=Engine
make: Entering directory `/home/stuart/CVS/AdventureGameStudio/Engine'
CFLAGS = -O2 -pie -fpie -g -fsigned-char -Wfatal-errors -DNDEBUG -DAGS_RUNTIME_PATCH_ALLEGRO -DAGS_HAS_CD_AUDIO -DAGS_CASE_SENSITIVE_FILESYSTEM -DALLEGRO_STATICLINK -DLINUX_VERSION -DDISABLE_MPEG_AUDIO -DBUILTIN_PLUGINS -DRTLD_NEXT -I/usr/include/freetype2 -I../Engine -I../Common -I../Common/libinclude -I../Plugins 

CXXFLAGS = -fno-rtti -Wno-write-strings -fpermissive -O2 -pie -fpie -g -fsigned-char -Wfatal-errors -DNDEBUG -DAGS_RUNTIME_PATCH_ALLEGRO -DAGS_HAS_CD_AUDIO -DAGS_CASE_SENSITIVE_FILESYSTEM -DALLEGRO_STATICLINK -DLINUX_VERSION -DDISABLE_MPEG_AUDIO -DBUILTIN_PLUGINS -DRTLD_NEXT -I/usr/include/freetype2 -I../Engine -I../Common -I../Common/libinclude -I../Plugins 

LDFLAGS = -Wl,--as-needed 

LIBS = -rdynamic -L/usr/lib/i386-linux-gnu -lalleg -laldmb -ldumb -Wl,-Bdynamic -ltheora -logg -lvorbis -lvorbisfile -lfreetype -logg -ldl -lpthread -lm -lc -lstdc++ 

make: *** No rule to make target `/usr/include/c++/4.7/i686-linux-gnu/bits/c++config.h', needed by `libsrc/hq2x/hq2x3x.o'. Stop.

Any ideas? Error of omission, something that's now obsolete with Raring, or something else?

---

### Post by Sslaxx on 2013-04-09
Going to bump this one up. Still getting this issue with 3.8.0-17.

Is this an issue with package changes in Ubuntu, obsolete dependencies in the AGS code, or something else?

---

### Post by dino99 on 2013-04-09
[http://feags.sourceforge.net/](http://feags.sourceforge.net/)
[http://www.adventuregamestudio.co.uk/forums/index.php?topic=46152.0](http://www.adventuregamestudio.co.uk/forums/index.php?topic=46152.0)

---

### Post by Sslaxx on 2013-04-09
Posted there already... [http://www.adventuregamestudio.co.uk/forums/index.php?topic=46152.msg636449503#msg636449503](http://www.adventuregamestudio.co.uk/forums/index.php?topic=46152.msg636449503#msg636449503)

---

### Post by steeldriver on 2013-04-09
It looks like libstdc++6-4.**7**-dev only has /usr/include/**i386**-linux-gnu/c++/4.7/bits/c++config.h

[http://packages.ubuntu.com/raring/i386/libstdc++6-4.7-dev/filelist](http://packages.ubuntu.com/raring/i386/libstdc++6-4.7-dev/filelist)

whereas libstdc++6-4.**6**-dev has /usr/include/c++/4.6/**i686**-linux-gnu/bits/c++config.h

[http://packages.ubuntu.com/raring/i386/libstdc++6-4.6-dev/filelist](http://packages.ubuntu.com/raring/i386/libstdc++6-4.6-dev/filelist)

I don't know if it's just a difference in terminology or if it means something deeper

---

### Post by Sslaxx on 2013-04-09
As well as the directory structure having changed between versions, too. Not that c++config.h is called directly by any of the relevant AGS source code files (as far as I can see).

If this is a Ubuntu packaging issue, I'm surprised more source code isn't falling over.

Actually, this is odd. There is no such directory called i686-linux-gnu (or i386-linux-gnu) listed as installed on my box. G++ 4.7, libstdc++6-6.4.7-dev installed. And I note that this did use to compile on this machine until recently. Am I missing something? Is this a bug? Or...?

---

