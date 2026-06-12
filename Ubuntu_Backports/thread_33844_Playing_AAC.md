---
title: "Playing AAC"
date: 2005-05-12
forum: Ubuntu Backports
---

### Post by mostwanted on 2005-05-12
Phew, I got a working libfaad2-0 package from Gismo before it was taken down for unknown reasons and seeing libfaad2-0 in backports (I'm guessing) I hesitated to update it, since it could mean my AAC would once again be unplayable in Rhythmbox. But I just couldn't stand the upgrade icon anymore, so I downloaded it and it worked! :D

Just thought I'd share with all o' them who have trouble with playing AAC files in Rhythmbox. It works now, guaranteed!

---

### Post by SKLP on 2005-05-13
Yeah, faad from backports works nicely :)

However, at the moment if you want to play AACs in muine, you have to build muine yourself. The muine binaries from ubuntu, it seems, have AAC support disabled. 
To build muine with AAC support this should work:

1. sudo apt-get build-dep muine (get the build dependencies for muine)

2. sudo apt-get install libfaad2-dev (install the libfaad development files)

However, the libfaad2-dev packages from ubuntu (and debian?) does not include the file mp4ff_int_types.h which is apperently needed in order to build muine with aac support.

3. So just get this file from here: [http://cvs.sourceforge.net/viewcvs.py/*checkout*/faac/faad2/common/mp4ff/mp4ff_int_types.h](http://cvs.sourceforge.net/viewcvs.py/*checkout*/faac/faad2/common/mp4ff/mp4ff_int_types.h) and store it somewhere, /usr/local/include is probably best

4. then get the tarball of the latest muine and run the standard ./configure && make && sudo make install combo :P

this worked for me (if I'm not forgetting anything). though it would be very nice if the muine package from ubuntu would have aac enabled... one can only dream :)

EDIT: breezy wishlist: libfaad2-dev needs to be fixed to include that file, and gstreamer0.8-faad should be in multiverse or something :)
also, muine should IMHO be compiled with AAC enabled...

---

### Post by mostwanted on 2005-06-07
^^ Could this perhaps be a request? Pretty please jdong :D I like Muine too.

*Bumps*

---

### Post by SKLP on 2005-07-08
[QUOTE=mostwanted]^^ Could this perhaps be a request? Pretty please jdong :D I like Muine too.

*Bumps*[/QUOTE]
Yea, that would be nice jdong.
I hope they (ubuntu) will compile it this way on breezy tho...

---

### Post by Slo Mo Snail on 2005-07-08
[QUOTE=SKLP]EDIT: breezy wishlist: libfaad2-dev needs to be fixed to include that file, and gstreamer0.8-faad should be in multiverse or something :)
also, muine should IMHO be compiled with AAC enabled...[/QUOTE]
I fixed the first one yesterday... now the package only needs to be approved by the MOTU ;) for the second one: afaik someone is working on that

---

### Post by SKLP on 2005-07-10
[QUOTE=Slo Mo Snail]I fixed the first one yesterday...[/QUOTE]Good work!
> for the second one: afaik someone is working on thatMay i ask who? :)

---

### Post by SKLP on 2005-08-01
*bump*

---

### Post by SKLP on 2005-08-09
Slo Mo Snail, I can see that your faad packages have hit breezy.
Muine still seems not to be built with them installed by default :(. EDIT: not sure about this.
When I have your packages of faad installed and run muine's ./configure i get
```
checking mp4ff.h usability... yes
checking mp4ff.h presence... yes
checking for mp4ff.h... yes

``` which is a lot better than with hoary's faad.  :) 

But when i compiled and installed it strangely still didn't seem to work.
So i thought maybe it was a bug in your packages (no offense).

So i installed the old faad packages and the file i mentioned in this thread (like I di d previously in hoary and that worked fine). BUT IT STILL DIDN'T WORK.

So I think I'm giving up on AAC+gnu/linux.
I'll be re-encoding all my music to mp3 (not ogg, cause of my ipod).

---

### Post by ahi on 2005-09-02
I found this problem as well: Muine doesn't recognize the
file type, even with the proper faad support compiled in. Try this patch:

```

diff -ur muine-0.8.3/libmuine/metadata.c muine-0.8.3.ahi/libmuine/metadata.c
--- muine-0.8.3/libmuine/metadata.c     2005-02-07 06:19:46.000000000 -0800
+++ muine-0.8.3.ahi/libmuine/metadata.c 2005-09-01 16:00:52.000000000 -0700
@@ -882,6 +882,7 @@
                m = assign_metadata_flac (escaped, error_message_return);
 #if HAVE_FAAD
        else if (!strcmp (info->mime_type, "application/x-m4a") ||
+                !strcmp (info->mime_type, "audio/mp4") ||
                 !strcmp (info->mime_type, "audio/x-m4a"))
                m = assign_metadata_mp4 (filename, error_message_return);
 #endif /* HAVE_FAAD */
```

---

