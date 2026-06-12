---
title: "Google Earth. Great Program that Works but has some bugs."
date: 2008-12-24
forum: The Cafe
---

### Post by stidmatt on 2008-12-24
One of my favorite programs on any OS is Google Earth. I like it a lot and on Ubuntu I downloaded it from Google's website. It would be nice if I could get it off Add/Remove Programs, to receive updates, but it works pretty well. However there are some bugs in it.

If you click on something to move where you are zoom in, or basically change anything the entire screen flashes black, I don't know what this is but it is pretty annoying.

When you click on a button to see some content it shows up white. You have to move your mouse over it and click or move your mouse wheel for it to show you the content.

Besides those two annoying features it is perfect. If they were fixed it would be a literally perfect program.

---

### Post by billgoldberg on 2008-12-24
> **stidmatt said:**
> One of my favorite programs on any OS is Google Earth. I like it a lot and on Ubuntu I downloaded it from Google's website. It would be nice if I could get it off Add/Remove Programs, to receive updates, but it works pretty well. However there are some bugs in it.

If you click on something to move where you are zoom in, or basically change anything the entire screen flashes black, I don't know what this is but it is pretty annoying.

When you click on a button to see some content it shows up white. You have to move your mouse over it and click or move your mouse wheel for it to show you the content.

Besides those two annoying features it is perfect. If they were fixed it would be a literally perfect program.

It's in the medibuntu repository.

Those problems are most likely caused by Compiz Fusion.

You can temporary disable compiz fusion if you are using Google Earth.

Press "alt+f2" and enter

```
metacity --replace
```

To switch back to Compiz Fusion, press "alt + f2" and enter

```
compiz --replace
```

---

### Post by oldos2er on 2008-12-24
Enable the Medibuntu repository ([http://medibuntu.org/](http://medibuntu.org/)) to get Googleearth with updates.

 If you're running compiz-fusion, try disabling it before running Googleearth, and see if that fixes your video issues.

---

