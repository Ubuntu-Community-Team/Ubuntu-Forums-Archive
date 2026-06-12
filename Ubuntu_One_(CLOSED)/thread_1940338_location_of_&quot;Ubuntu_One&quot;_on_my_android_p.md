---
title: "location of &quot;Ubuntu One&quot; on my android phone ?"
date: 2012-03-13
forum: Ubuntu One (CLOSED)
---

### Post by ghat on 2012-03-13
hi

I haved ssh'd into my android phone and frantically searching for the folder equivalent of "~/Ubuntu One" on the desktop...

where is this located ?

G

---

### Post by duanedesign on 2012-03-20
On my phone it is:

```
/sdcard/u1/Ubuntu One
```

---

### Post by a_flj_ on 2012-04-26
I just installed UbuntuOne, on an Ubuntu PC and on an Android phone (Galaxy Nexus), and there is no folder /sdcard/u1/ on the Nexus, although the U1 client does show the files I added to ~/Ubuntu One on my PC.

Anybody any advice?

I'm not using the default media players, and I also want to synchronize text files. If I can't browse the files on the android device, Ubuntu One is useless for me.

---

### Post by gentao88 on 2012-04-27
What I do and works:
On the android u1 app, tap on the file or continiously tap on the folder you would like to download to your phone. After that, the file/folder will be placed at /sdcard/u1/
Seems like the files are not synced if you do not select to download them
Hope that i helped

---

### Post by mkarnicki on 2012-04-30
That is correct. You can download files (or flat-download of directories), which will appear under /mnt/sdcard/u1 directory (root of all Ubuntu One cloud folders, including "~/Ubuntu One" itself). Although we don't sync your content back to U1, we hope to implement that soon, so stay tuned for more :)

---

