---
title: "Opensong not available for 64bit"
date: 2009-06-30
forum: Ubuntu Christian Edition
---

### Post by david_kt on 2009-06-30
Unfortunately, opensong only available for 32 bit:

[http://sourceforge.net/forum/forum.php?thread_id=3264270&forum_id=373379](http://sourceforge.net/forum/forum.php?thread_id=3264270&forum_id=373379)
> At this moment it is not possible to create a 64bit version with the current development environment. It is however no problem to run OpenSong on a 64bit Windows or MacOS machine. Linux is more of a problem.

So, if I include it in ubuntu-ce, it would make ubuntu-ce only available for 32bit. Any opinion?

DK

---

### Post by jonathonblake on 2009-06-30
> **david_kt said:**
> Unfortunately, opensong only available for 32 bit:

32 bit is somewhere between five and ten years out of date. 

If 32 bit is supported, it should be done only for _legacy_ reasons. IOW, treat it (32 bit) as if it was i386 architecture, and justify 32 bit support accordingly.

jonathon

---

### Post by shane2peru on 2009-06-30
Only thing I can come up with is just to leave OpenSong out for the 64bit side, and let them know it isn't available for 64bit.  I know 32bit software can be run on 64bit, I just am not 100% sure how to go about it, and what problems it could cause.

Shane

---

### Post by david_kt on 2009-06-30
> **shane2peru said:**
> Only thing I can come up with is just to leave OpenSong out for the 64bit side, and let them know it isn't available for 64bit.  I know 32bit software can be run on 64bit, I just am not 100% sure how to go about it, and what problems it could cause.

Shane

The good news is you could run OpenSong Portable using wine. It is better to use wine-Esword prefix (created using my installer) as it solve richedit problem:

1. Download opensong portable [here]("http://hivelocity.dl.sourceforge.net/sourceforge/opensong/OpenSong-V1.5.1-Portable.zip")
2. Extract it.
3. Launch it with command:
```

env WINEPREFIX="$HOME/.wine_Esword" wine /Path_/to_/OpenSong.exe
```

You could run it in default wine as well, but you need native riched20 to avoid richedit fixme message (not sure yet the implication of this fixme message).

I have not tried the windows version using installer file. It should be ok as well.

DK

---

### Post by Mickeyj4j on 2010-07-26
> **david_kt said:**
> The good news is you could run OpenSong Portable using wine. It is better to use wine-Esword prefix (created using my installer) as it solve richedit problem:

1. Download opensong portable [here]("http://hivelocity.dl.sourceforge.net/sourceforge/opensong/OpenSong-V1.5.1-Portable.zip")
2. Extract it.
3. Launch it with command:
```

env WINEPREFIX="$HOME/.wine_Esword" wine /Path_/to_/OpenSong.exe
```

You could run it in default wine as well, but you need native riched20 to avoid richedit fixme message (not sure yet the implication of this fixme message).

I have not tried the windows version using installer file. It should be ok as well.

DK

there is a more tailored version of opensong from Portable apps try this [http://portableapps.com/node/13747](http://portableapps.com/node/13747).  the portable apps menu runs from a usb adn in wine as well as windoes. its the perfect solution. especially if you want to use opensong on other os.

---

### Post by FredJukilo on 2012-04-03
Hi guys..
It's simple....
open a shell 

sudo su

dpkg -i --force-architecture opensong_1.6.2-1_i386.deb 



It works......!!!!!!!!

Bye

---

### Post by stlsaint on 2012-04-04
> **FredJukilo said:**
> Hi guys..
It's simple....
open a shell 

sudo su

dpkg -i --force-architecture opensong_1.6.2-1_i386.deb 



It works......!!!!!!!!

Bye

This is a dangerous command and it is not recommended nor supported to mix architectures!!

---

