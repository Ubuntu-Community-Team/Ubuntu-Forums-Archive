---
title: "Not playing mp3 songs"
date: 2009-07-24
forum: Wine
---

### Post by satishsaley on 2009-07-24
I have installed UBUNTU9.04 inside windows XP.I am having startup sound in UBUNTU and i can play .waw files,but unable to play mp3 files.Can anyone help me,please.Also tell me,can i access internet from UBUNTU in case it is installed inside Windows XP?If yes,how?:confused:

---

### Post by prshah on 2009-07-24
> **satishsaley said:**
> I have installed UBUNTU9.04 inside windows XP.I am having startup sound in UBUNTU and i can play .waw files,but unable to play mp3 files.Can anyone help me,please.Also tell me,can i access internet from UBUNTU in case it is installed inside Windows XP?If yes,how?:confused:

You need to install the ubuntu-restricted-extras package to use mp3 (and various other audio/video formats). To do this, open a terminal (Applications-Accessories-Terminal) and give the command ```
sudo apt-get install ubuntu-restricted-extras
```

Note that you will need an Internet connection for this.

You can use Internet in a Wubi (within windows) install. For the exact steps, we need to know how you use Internet in Windows. 

Most likely the Internet will already be activated and working in Ubuntu. Try to browse a site such as [www.google.com](www.google.com) using firefox. 

Post back with your Internet access details for more specific advice.

---

### Post by hkvn on 2009-07-24
In this case, You can open Add/remove Programe and install all gstreamer codecs to play mp3, wma, ..

P/S: Why is this topic in wine box?

---

