---
title: "Sony raw-files (arw) and ufraw doesn't work!"
date: 2008-06-29
forum: Ubuntu Studio
---

### Post by foof on 2008-06-29
Why do I only get distorted blur when trying to open images from my new camera (Sony A200)? It is the raw file format called .arw

I try to open it in Gimp with ufraw 0.13 installed from the repo.

Any ideas?

---

### Post by swisscow on 2008-06-30
Funny enough, looking at a similar picture myself now. Did some reading, sony arw support is supposed to be added to the next release of ufraw. In the meantime, have a look at Rawstudio and RawTherapee. Both read the arw files form my sony a200 without a hitch

---

### Post by Necrotrup on 2008-08-17
Try rawstudio. I have the same problem when try to use ufraw, but I can open .arw files and work in rawstudio.

---

### Post by carusoswi on 2009-02-07
> **Necrotrup said:**
> Try rawstudio. I have the same problem when try to use ufraw, but I can open .arw files and work in rawstudio.

Interesting.  I own an A100 and an A700.  I use UfRaw in Ubuntu 8.10 all the time to open RAW files from both cameras.  No luck with rawstudio or rawtherapee so far.  The files show up, but they are greyed out.  Am I doing something wrong?

It's curious that our problems seem to mirror each other.

Caruso

---

### Post by carusoswi on 2009-02-07
> **carusoswi said:**
> Interesting.  I own an A100 and an A700.  I use UfRaw in Ubuntu 8.10 all the time to open RAW files from both cameras.  No luck with rawstudio or rawtherapee so far.  The files show up, but they are greyed out.  Am I doing something wrong?

It's curious that our problems seem to mirror each other.

Caruso

Actually, the above is not accurate.  When I navigate to a folder containing RAW Sony files, nothing shows up until I use the preference button to select all file types.  Then, the files show up, are selectable, but, when I click to open them, the work area remains blank.

Help would be appreciated.

Caruso

---

### Post by Incompetnce on 2009-03-09
UFRaw didn't work for me either! (Also, RAW photos were displaying like the picture above in F-spot photo manager. Rawstudio works fine, however!

Although the settings it automatically selects look all wrong and I have to fiddle a lot with each picture. That might just be because I'm not a great photographer...

---

### Post by kayosiii on 2009-03-09
all these products rely on dcraw... So check DCRaw for compatibility.. If dcraw does support it - check what version it is supported in - You will need to wait for your raw converter to use that version of dcraw.

---

