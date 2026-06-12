---
title: "Compiling Wine with a specific patch."
date: 2010-08-16
forum: Wine
---

### Post by xenogia on 2010-08-16
I am just wondering how you would go about compiling Wine from Scratch on Ubuntu 10.04 Lucid with a specific patch as I need to do this for a specific application.

The patch in question is here:
[http://bugs.winehq.org/show_bug.cgi?id=14882](http://bugs.winehq.org/show_bug.cgi?id=14882)

Any step by step guide would be greatly appreciated.

---

### Post by beastrace91 on 2010-08-16
Download and extract the Wine source for the version of Wine you wish to patch. Open a terminal and navigate to the directory of your extracted contents.

Then try the following in terminal:

```
wget http://bugs.winehq.org/attachment.cgi?id=29820
mv attachment* patch.diff
patch -p1 < patch.diff
./configure && make depend && make
sudo make install
```

Regards,
~Jeff Hoogland

---

