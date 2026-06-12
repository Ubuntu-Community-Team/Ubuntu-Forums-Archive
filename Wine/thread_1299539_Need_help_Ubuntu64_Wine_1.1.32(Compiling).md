---
title: "Need help Ubuntu64 Wine 1.1.32(Compiling)"
date: 2009-10-24
forum: Wine
---

### Post by grndzro on 2009-10-24
Ne1 figure out how to compile wine on Ubuntu 9.10?

I got the lmpg123 bug.

nel32  ../../libs/port/libwine_port.a -lmpg123  
mpegl3.o: In function `MPEG3_Reset':
/home/gz/Desktop/wine1.1.32/dlls/winemp3.acm/mpegl3.c:401: undefined reference to `mpg123_feedseek'
collect2: ld returned 1 exit status
winegcc: gcc failed
make[2]: *** [winemp3.acm.so] Error 2
make[2]: Leaving directory `/home/gz/Desktop/wine1.1.32/dlls/winemp3.acm'
make[1]: *** [winemp3.acm] Error 2
make[1]: Leaving directory `/home/gz/Desktop/wine1.1.32/dlls'
make: *** [dlls] Error 2

---

### Post by maaddog on 2009-10-26
Try this:

    mpg123_feedseek(aad->mh, 0, SEEK_SET, NULL);
to
    mpg123_feedseek_64(aad->mh, 0, SEEK_SET, NULL);

in mpegl3.c

Testing now, its compiled okay =)

---

### Post by geektanic on 2009-11-10
> **maaddog said:**
> Try this:

    mpg123_feedseek(aad->mh, 0, SEEK_SET, NULL);
to
    mpg123_feedseek_64(aad->mh, 0, SEEK_SET, NULL);

in mpegl3.c

Testing now, its compiled okay =)

This was exactly it for my issue - Thanks Maaddog

---

