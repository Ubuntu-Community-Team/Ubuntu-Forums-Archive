---
title: "Two questions on UbuntuOne"
date: 2009-11-05
forum: Ubuntu One (CLOSED)
---

### Post by Vyrlokar on 2009-11-05
First at all, how does UbuntuOne deal with conflicts? If I have two machines associated to the same UbuntuOne account, modify a shared file on both at the same time, and then they sync (because the modification was done while offline) how will UbuntuOne react? Will it ask me? Will it create a copy of the file, so I now have twice as much space used?

Second, I run Ubuntu NBR on my netbook, and Kubuntu on my desktop. Can I run UbuntuOne on the Kubuntu desktop? All installers I've seen seem to be for GNOME.

---

### Post by awam66 on 2009-11-05
> **Vyrlokar said:**
> First at all, how does UbuntuOne deal with conflicts? If I have two machines associated to the same UbuntuOne account, modify a shared file on both at the same time, and then they sync (because the modification was done while offline) how will UbuntuOne react? Will it ask me? Will it create a copy of the file, so I now have twice as much space used?

As far as I understand it it syncs on the file datestamp. Someone will correct me if I'm wrong. It will not create a second file.

---

### Post by tcole on 2009-11-05
It depends. If the same file gets changed in two separate locations, though, a second file with a name ending in .u1conflict may appear.

As far as the other question -- Kubuntu installation isn't as slick as it should be, but it can be made to work. Install ubuntuone-client-gnome, and then from konsole run:

```
ubuntuone-client-applet 2> /dev/null &
```

---

### Post by NUboon2Age on 2010-07-01
Here's how I got Kubuntu (Lucid) running UbuntuOne using the gnome client: 

[http://ubuntuforums.org/showthread.php?p=9535765#post9535765](http://ubuntuforums.org/showthread.php?p=9535765#post9535765)

---

### Post by duanedesign on 2010-07-01
If a situation arises where there is a conflict it will create a copy of the file with the extension u1conflict. This means it wont make the decision for you, but allows you to decide which to keep. The way to resolve conflicts is to pick from the original file (if there is one) and the conflict file the version that you wish to keep and to delete the conflict file or move the conflict file over the original one, depending on tour choice.

How do you select which file you want to keep? That really depends on the kind of files you have.

.u1conflict[.NN] files are ignored by ubuntuone. So you can either leave them around or delete them if you dont need them.

---

