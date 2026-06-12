---
title: "SOrt of stupid question, but how do I uninstall KDE?"
date: 2005-09-04
forum: The Cafe
---

### Post by xequence on 2005-09-04
I installed KDE a week ago and I very much dont like it... NOut very customizable and its slower then gnome. How do I uninstall it?

I havnt asked a question in awhile so, thanks :)

---

### Post by xmastree on 2005-09-04
How did you install it? through synaptic?
Go to synaptic, search for kde and mark for complete removal.

---

### Post by WildTangent on 2005-09-04
sudo apt-get remove kubuntu-desktop should do the trick

-Wild

---

### Post by SKLP on 2005-09-04
[QUOTE=WildTangent]sudo apt-get remove kubuntu-desktop should do the trick

-Wild[/QUOTE]No, it shouldn't.

---

### Post by Brunellus on 2005-09-04
[QUOTE=xequence]I installed KDE a week ago and I very much dont like it... NOut very customizable and its slower then gnome. How do I uninstall it?

I havnt asked a question in awhile so, thanks :)[/QUOTE]
 I already asked this not so long ago.  Here's the relevant thread:


[http://www.ubuntuforums.org/showthread.php?t=57378&highlight=debfoster](http://www.ubuntuforums.org/showthread.php?t=57378&highlight=debfoster)

use debfoster.  Essentially, you will be choosing which package groups stay and which go.

---

### Post by Knome_fan on 2005-09-04
Simply uninstall kdelibs

That's all you need.

---

### Post by xequence on 2005-09-04
Thanks everyone. I was going to do it in synaptic then I realised, I have to check every single one. What if I miss some and it doesent accually uninstall :)

Im gonna use the debfoster thingy :)

---

### Post by Knome_fan on 2005-09-04
You don't seem to believe me, but you really only need to uninstall kdelibs and all kde stuff will automatically be uninstalled as it depends on kdelibs.

Oh, and deborphan is nicer than debforster imho.

---

