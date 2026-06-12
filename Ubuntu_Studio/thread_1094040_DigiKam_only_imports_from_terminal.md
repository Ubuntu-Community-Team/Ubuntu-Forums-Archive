---
title: "DigiKam only imports from terminal"
date: 2009-03-12
forum: Ubuntu Studio
---

### Post by oygle on 2009-03-12
I have used DigiKam for a while now, and have several albums. Tried to get it to import photos, but it refused to import, even though it auto recognised the camera. Only F-Spot was able to get thumbnails. I tried all sorts of things, powering the camera off and on, removing the camera from Digikam and then let it aoto select, etc,ect.

Then I ram DigiKam from the terminal, and no problems, it showed the thumbnails and is importing the pics.

Why will it only work in terminal mode ?  I'm not using 'sudo', just ran the command 'digikam'.

Looked what the menu has setup fro DigiKam, and it was

```
digikam -caption "%c" %i
```

Oygle

---

### Post by oygle on 2009-03-12
This won't mount either, as a USB would normally mount.

It's not shown under the /media path, but has a location of

> gphoto2://[usb:004,012]/DCIM

---

