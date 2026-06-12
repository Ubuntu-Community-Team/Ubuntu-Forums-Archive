---
title: "zsync freeze"
date: 2021-08-18
forum: Ubuntu Development Version
---

### Post by VMC on 2021-08-18
I'm finding of late that this location for ubuntu freezes
All the others work: kubuntu, lubuntu, mate, etc. Only ubuntu fails to advance the amount to be updated:
```
zsync -i ubuntu.iso [http://cdimage.ubuntu.com/daily](http://cdimage.ubuntu.com/daily)-live/current/impish-desktop-amd64.iso.zsync -o ubuntu.iso
```

But if I use heanet, it always updates ubuntu:
```
zsync -i ubuntu.iso [http://ftp.heanet.ie/mirrors/ubuntu-cdimage/daily-live/pending/impish](http://ftp.heanet.ie/mirrors/ubuntu-cdimage/daily-live/pending/impish) -desktop-amd64.iso.zsync -o ubuntu.iso
```
Anyone else see this?

(ps- having issues with code tags. keeps inserting after http)

---

### Post by sudodus on 2021-08-18
At this link: [http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/) you can see that Ubuntu has the 'current' and 'pending' subdirectories.

Right now, when I check, they happen to contain the same version, but sometimes (maybe even often) the current version is lagging behind the pending one (I guess depending on when the automatic testing is performed and if it is successful).

I have been using the cdimage link successfully. I think it was 'only' some temporary error, when it failed for you, but thanks for the heads up - maybe next time I'll be affected by it, and then I'll try your workaround with the heanet.ie link or some other mirror.

---

### Post by VMC on 2021-08-18
Its been happening for days now. Has nothing to do with 'current', 'pending', 'date'. It just hangs right after it reads the input file. Must be something on my end.
edit: tried again right now using "http://cdimage.ubuntu.com/daily-live...", and this time it worked.

---

