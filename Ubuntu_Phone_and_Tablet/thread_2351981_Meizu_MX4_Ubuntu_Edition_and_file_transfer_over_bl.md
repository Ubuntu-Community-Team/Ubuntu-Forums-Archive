---
title: "Meizu MX4 Ubuntu Edition and file transfer over bluetooth"
date: 2017-02-08
forum: Ubuntu Phone and Tablet
---

### Post by stefan_bahrens on 2017-02-08
It isn't possible to send or receive files via bluetooth using the MX4. It is possible to connect to bluetooth headphones from the MX4 to play mp3 file so there is some minimal functionality there. Does anyone know if Canonical intend to add this fairly basic functionality in a future update? It seems odd not to be able to move data files back and forth.

---

### Post by stefan_bahrens on 2017-02-10
Has anyone found a way to transfer files to and from this Ubuntu phone? Thanks for any help.

---

### Post by krusty8 on 2017-02-11
Should be possible with a USB cable. Alternatively via ssh or adb.

---

### Post by stefan_bahrens on 2017-02-13
Thanks for the reply krusty8. I should have written -
"Has anyone found a way to transfer files to and from this Ubuntu phone using bluetooth?"
I assume from your reply this is simply impossible. Can you tell me what adb is please.
I've never heard of it. Thanks again.

---

### Post by krusty8 on 2017-02-13
> **krusty8 said:**
> Should be possible with a USB cable. 

Just to be clear - What I meant here was: Plug the phone with a usb cable into your computer. A notification or the file browser of your operating system should pop up and let you move files around. That's it. Have you tried?

Regarding bluetooth : No, I didn't mean to imply that this is not possible. I simply do not know.

Regarding adb : That's "Android Debug Bridge". Basically a command line tool that allows you (among other things) to push/pull files. See, e.g., [https://www.youtube.com/watch?v=LLjeC1bXKxU](https://www.youtube.com/watch?v=LLjeC1bXKxU) It might, or it might not be your cup of tea ;) (ssh - a bit more "standard" than adb, but commandline nevertheless)

Hth!

---

### Post by krusty8 on 2017-02-13
> **stefan_bahrens said:**
> I assume from your reply this is simply impossible. 

According to a quick internet search it seems that [out of the box it's not possible]("https://bugs.launchpad.net/canonical-devices-system-image/+bug/1511525"), but [maybe if you install this tool]("https://open.uappexplorer.com/app/ubtd.mzanetti").

---

### Post by dumazdamaz on 2017-02-14
most likely also with bluetoothctl from the terminal app. but, of course, a little bit inconvenient

---

### Post by mily2 on 2017-02-22
Have you tried this app?
[https://open.uappexplorer.com/app/ubtd.mzanetti](https://open.uappexplorer.com/app/ubtd.mzanetti)

---

### Post by fallenshadow on 2017-02-27
No functionality built in for this, as I discovered recently. Pretty crazy to not have this since day one.

---

### Post by stefan_bahrens on 2017-03-09
Thanks very much for all these suggestions. I'll try adb if I can figure it out. It seems odd to have bluetooth for headphones but not file transfer. Anyway, much appreciated. Thanks again.

---

