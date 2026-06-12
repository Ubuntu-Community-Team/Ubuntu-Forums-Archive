---
title: "Need help creating dvd file system"
date: 2006-07-03
forum: The Cafe
---

### Post by teia on 2006-07-03
Hi

I downloaded this dvd-rar file and it contains a heap of smaller rar files. When I unpacked the files into a directory it created a lot of files, but no file system with directories.
All the files needed for a dvd seems to be in place, including menues, but I guess I need to put the files into some directories to get a real dvd structure that my player can read.

Now, can anybody tell me how to create the correct structure and where to put the different files?

I have tried different solutions, but still my player refuse to play the dvd.


Thanks

Teia

---

### Post by kabus on 2006-07-03
I guess you have a bunch of files that look like this ? :

```
VIDEO_TS.BUP  VTS_01_0.BUP  VTS_01_1.VOB  VTS_01_3.VOB  VTS_01_5.VOB
VIDEO_TS.IFO  VTS_01_0.IFO  VTS_01_2.VOB  VTS_01_4.VOB
```

If so, create a new directory named dvd (or whatever) with two subdirs named AUDIO_TS and VIDEO_TS. 
Move all the files to VIDEO_TS (AUDIO_TS is only important for compatibility with some finicky old dvd players).

Then create the image :
```

mkisofs -dvd-video -o dvdimage.iso dvd/
```

You can burn it with :
```

growisofs -dvd-compat -Z /dev/hdx=dvdimage.iso
```

(/dev/hdx = your dvd burner)

---

### Post by teia on 2006-07-03
Wow it worked

Thanks alot pal you're the greatest\\:D/ \\:D/ \\:D/ \\:D/ 

Teia

---

