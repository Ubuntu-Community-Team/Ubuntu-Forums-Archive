---
title: "MP3 in Wine"
date: 2010-01-24
forum: Wine
---

### Post by Cannonball Java on 2010-01-24
I just switched to Kubuntu (from Windows) about a month ago. I am loving it and have only ran into one problem. That issue is Audiosurf. MP3s do not work on it, or any other windows program for that matter. They do, however, work on version 1.1.28 and earlier of wine. I'm pretty sure its an issue with libmpg123, as wine started to use it in version 1.1.29. Does anyone know how I could get MP3 functionality in later versions of wine? I am running Karmic Kubuntu on a 64 bit arch, if that helps any. Thanks in advance!

---

### Post by beastrace91 on 2010-01-24
There is a patch for building Wine on 64bit with mp3 support - I use it personally to play Morrowind :)

[http://ubuntuforums.org/showpost.php?p=8503423&postcount=5](http://ubuntuforums.org/showpost.php?p=8503423&postcount=5)

Note that this will require compiling Wine from source.

Regards,
~Jeff

---

### Post by Cannonball Java on 2010-01-24
Ah, thanks! That should have done the trick. Unfortunately, I'm now getting page fault errors in Audiosurf. I just installed it in it's own v.1.1.28 prefix and it works like a charm though! At least other MP3 programs should work for me now.

---

