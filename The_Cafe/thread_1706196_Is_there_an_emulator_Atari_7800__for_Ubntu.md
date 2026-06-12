---
title: "Is there an emulator Atari 7800  for Ubntu ?"
date: 2011-03-13
forum: The Cafe
---

### Post by honeybear on 2011-03-13
There is all emulators, but I cannot find one for Atari 7800.

Regards

---

### Post by honeybear on 2011-03-13
I found some sources, but it is only for Windows. Could someone code it to linux or code something equivalent ? 

[https://home.comcast.net/~gscottstanton/](https://home.comcast.net/~gscottstanton/)

PSP has this one: [http://zx81.zx81.free.fr/public/caanoo/a7800/caanoo-a7800-v1.1.0-src.zip](http://zx81.zx81.free.fr/public/caanoo/a7800/caanoo-a7800-v1.1.0-src.zip)
can you make it work for ubuntu please?

---

### Post by mips on 2011-03-13
[MESS]("http://www.mess.org/") Linux/Mac uses SDLMESS [http://rbelmont.mameworld.info/?page_id=163](http://rbelmont.mameworld.info/?page_id=163)
[http://mess.redump.net/supported_systems](http://mess.redump.net/supported_systems)

ProSystem port to SDL [http://www.atariage.com/forums/topic/99280-prosystem-source-code-now-available/page__st__25__p__1218398#entry1218398](http://www.atariage.com/forums/topic/99280-prosystem-source-code-now-available/page__st__25__p__1218398#entry1218398)

---

### Post by honeybear on 2011-03-13
> **mips said:**
> [MESS]("http://www.mess.org/") Linux/Mac uses SDLMESS [http://rbelmont.mameworld.info/?page_id=163](http://rbelmont.mameworld.info/?page_id=163)
[http://mess.redump.net/supported_systems](http://mess.redump.net/supported_systems)

thank you
wow prosystem exists really for LINUX!!  That s cool because it is the very best emu of 7800!

however I am not capable to compile. Does someone would have a deb for ubuntu for that sdl prosystem emulator? 
```

ProSystem port to SDL [http://www.atariage.com/forums/topic/99280-prosystem-source-code-now-available/page__st__25__p__1218398#entry1218398](http://www.atariage.com/forums/topic/99280-prosystem-source-code-now-available/page__st__25__p__1218398#entry1218398)

minizip/ioapi.c:102: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;fwrite_file_func&#8217;
minizip/ioapi.c:104: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;stream&#8217;
minizip/ioapi.c:105: error: conflicting types for &#8216;buf&#8217;
minizip/ioapi.c:93: note: previous declaration of &#8216;buf&#8217; was here
minizip/ioapi.c:106: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;size&#8217;
minizip/ioapi.c:107: error: expected identifier or &#8216;(&#8217; before &#8216;{&#8217; token
minizip/ioapi.c: In function &#8216;ftell_file_func&#8217;:
minizip/ioapi.c:114: error: expected declaration specifiers before &#8216;voidpf&#8217;
minizip/ioapi.c:115: error: expected declaration specifiers before &#8216;voidpf&#8217;
minizip/ioapi.c: In function &#8216;fseek_file_func&#8217;:
minizip/ioapi.c:123: error: expected declaration specifiers before &#8216;voidpf&#8217;
minizip/ioapi.c:124: error: expected declaration specifiers before &#8216;voidpf&#8217;
minizip/ioapi.c:125: error: expected declaration specifiers before &#8216;uLong&#8217;
minizip/ioapi.c: In function &#8216;fclose_file_func&#8217;:
minizip/ioapi.c:149: error: expected declaration specifiers before &#8216;voidpf&#8217;
minizip/ioapi.c:150: error: expected declaration specifiers before &#8216;voidpf&#8217;
minizip/ioapi.c: In function &#8216;ferror_file_func&#8217;:
minizip/ioapi.c:158: error: expected declaration specifiers before &#8216;voidpf&#8217;
minizip/ioapi.c:159: error: expected declaration specifiers before &#8216;voidpf&#8217;
minizip/ioapi.c: In function &#8216;fill_fopen_filefunc&#8217;:
minizip/ioapi.c:167: error: expected declaration specifiers before &#8216;zlib_filefunc_def&#8217;
minizip/ioapi.c:169: error: invalid type argument of &#8216;->&#8217; (have &#8216;int&#8217;)
minizip/ioapi.c:169: error: &#8216;fopen_file_func&#8217; undeclared (first use in this function)
minizip/ioapi.c:169: error: (Each undeclared identifier is reported only once
minizip/ioapi.c:169: error: for each function it appears in.)
minizip/ioapi.c:170: error: invalid type argument of &#8216;->&#8217; (have &#8216;int&#8217;)
minizip/ioapi.c:170: error: &#8216;fread_file_func&#8217; undeclared (first use in this function)
minizip/ioapi.c:171: error: invalid type argument of &#8216;->&#8217; (have &#8216;int&#8217;)
minizip/ioapi.c:171: error: &#8216;fwrite_file_func&#8217; undeclared (first use in this function)
minizip/ioapi.c:172: error: invalid type argument of &#8216;->&#8217; (have &#8216;int&#8217;)
minizip/ioapi.c:173: error: invalid type argument of &#8216;->&#8217; (have &#8216;int&#8217;)
minizip/ioapi.c:174: error: invalid type argument of &#8216;->&#8217; (have &#8216;int&#8217;)
minizip/ioapi.c:175: error: invalid type argument of &#8216;->&#8217; (have &#8216;int&#8217;)
minizip/ioapi.c:176: error: invalid type argument of &#8216;->&#8217; (have &#8216;int&#8217;)
make: *** [minizip/ioapi.o] Error 1
```

---

