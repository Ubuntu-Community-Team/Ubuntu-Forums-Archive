---
title: "A Wine version that works out of the box with Karmic?"
date: 2010-05-24
forum: Wine
---

### Post by desconocido on 2010-05-24
Is there a version of Wine that works out of the box with a non-upgraded install of Ubuntu Karmic 9.10 desktop?

I ask because I am trying to install Wine on a computer that does not have internet access and I am not getting on very fast. (See [http://forum.winehq.org/viewtopic.php?p=43875](http://forum.winehq.org/viewtopic.php?p=43875))

Thanks in advance

Sorry for any "cross-pasting" as I believe it is called.

---

### Post by cogadh on 2010-05-24
The problem you are going to have installing any of the Wine packages on a machine without internet access is the inability to get the additional dependency packages installed at the same time. If would be easiest, if at all possible, to temporarily get the machine on the internet, install Wine, then take it offline. 

If that is not possible, then use your machine with internet access to check which packages Wine depends on, then download each of those packages from the [Ubuntu repository]("http://packages.ubuntu.com/"), copy them to a thumb drive or burn to CD/DVD and manually install each one on the offline computer. Of course, you might then run into dependency problems for some of the packages Wine depends on and you might have to do the whole process multiple times.

---

### Post by mac9416 on 2010-05-25
Hello, desconocido,

You can use [Keryx]("http://keryxproject.org") to download Wine and its dependencies to install on your offline computer.

---

