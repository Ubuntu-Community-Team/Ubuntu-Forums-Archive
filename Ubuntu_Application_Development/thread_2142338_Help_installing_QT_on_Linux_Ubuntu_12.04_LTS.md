---
title: "Help installing QT on Linux Ubuntu 12.04 LTS"
date: 2013-05-05
forum: Ubuntu Application Development
---

### Post by Bresser on 2013-05-05
Ok so I dowloads QT5 from their website and it gave me a .run file. I went into terminal and 
```
chmod u+x qt.run
./qt.run

```
*then it said no marker found, stopped after 1.00MiB*
can anyone tell me why it is doing this.

---

### Post by 2F4U on 2013-05-05
Did you post the commands exactly as you really entered them? Since there is a blank in qt.run which shouldn't be there.

---

### Post by Bresser on 2013-05-05
yes that is exactly how I entered it except i used
```

cd

```
to get into the Downloads directory.

---

### Post by steeldriver on 2013-05-05
did you check the md5sum of the download? that error sounds like the kind of thing you'd get with an incomplete archive

---

### Post by Bresser on 2013-05-05
I will be honest bud. I have no idea what a md5sum is

---

### Post by steeldriver on 2013-05-05
```

$ cd ~/Downloads
$ md5sum qt-linux-opensource-5.0.2-x86-offline.run 
[COLOR=#0000ff]**f4ff26e65e7229e514c72e2eaf6743a0  **[/COLOR]qt-linux-opensource-5.0.2-x86-offline.run

```

and compare the long string of hex digits with the value given in the (info) link on the relevant Qt download page e.g.

[http://download.qt-project.org/official_releases/qt/5.0/5.0.2/qt-linux-opensource-5.0.2-x86-offline.run.mirrorlist](http://download.qt-project.org/official_releases/qt/5.0/5.0.2/qt-linux-opensource-5.0.2-x86-offline.run.mirrorlist)

If they are not the same then something went wrong with the download

---

