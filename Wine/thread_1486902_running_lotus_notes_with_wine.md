---
title: "running lotus notes with wine"
date: 2010-05-18
forum: Wine
---

### Post by jml52187 on 2010-05-18
howdy all,
when trying to browse C: with wine, I get the following message:

Unable to run the command specified. The file or folder file:///home/user/Documents/.wine/dosdevices/c: does not exist.

I was wondering how I screwed that up. My end goal is to be free of windoze, and all I need is the ability to run AutoCAD and lotus notes. Any help would be appreciated.
thanx,
J

---

### Post by Chesamo on 2010-05-18
You know there's a Linux version of Notes out, right?

Either way, the file path shouldn't be ```
/home/user/Documents/.wine/dosdevices/c:
``` it should be ```
/home/user/Documents/.wine/dosdevices/drive_c
```

---

### Post by jml52187 on 2010-05-18
I tried to install the linux tarfile on my 8.04 host but either the file was broken or something to that effect. It got through around 86% and was extracting files when it died. crashed on me several times. This attempt is kind of a last ditch effort before my boss goes out and buys 6 windoze xp machines to operate this system.

and I'm rambling. now to figure out how to correct that path. Any suggestions? I am quite the newbie

Thanx again,
J

---

### Post by Chesamo on 2010-05-18
Assuming the default Program Files installation directory is the same from when I worked at IBM/Lotus (about a year ago), the directory should be ```
 /home/user/Documents/.wine/dosdevices/drive_c/Program\ Files/IBM/Notes
``` Pay attention when you're running the installer and it'll tell you where it is.

**EDIT IMPORTANT!** It should NOT be ```
/home/user/Documents/.wine/...
``` it should be ```
/home/user/.wine/...
``` The WINE configuration is not in the Documents folder, it's right in the home folder.

---

