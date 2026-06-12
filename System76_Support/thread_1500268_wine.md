---
title: "wine"
date: 2010-06-02
forum: System76 Support
---

### Post by porlaizquierda on 2010-06-02
i tried to install vlc on my psp using wine. it didn't work and my starling netbook is working without a problem, as is wine. but when i went to the wine folder i found what you see in the attachments. i tried manually finding stuff, but the folder does not exist, and i tried deleting wine, but the folder is still there, along with all those vlc files. so i reinstalled anyway. like i said, i'm not having problems, but i do like to get rod of extraneous stuff. look especially at screenshot-2. can anyone help? i'm using 9.10 by the way. would upgrading get rid of all that?

---

### Post by porlaizquierda on 2010-06-02
i also tried uninstalling it using the uninstall wine software, but that didnot work either.

---

### Post by dtfinch on 2010-06-03
Why not install the native VLC from the repository rather than running the Windows port on Wine?

That is odd that it created so many shortcuts. There's a menu editor (maybe Main Menu in preferences) you can use to remove or hide them. Where is "e:" pointing to?

---

### Post by porlaizquierda on 2010-06-03
like i said i was trying to install it on my psp via wine. what do you mean where is c: pointing to? do you mean this?

home/degobrah/.wine/dosdevices/e:/VIDEO/VLC' (No such file or directory)

---

### Post by betrunkenaffe on 2010-06-03
Is this in the right forum? Seems to me it should be in the wine support one.

And the question still stands that if you are running linux, why would you opt for the windows vlc player over the linux native vlc player (which does not require wine)

---

### Post by thomasaaron on 2010-06-03
Yeah, wine's package management (if you can call it that) is pretty poor. If you want a fresh start, just uninstall wine using Synaptic Package Manager.

Then, open a terminal and run...

rm -r .wine

Then, re-install wine.

---

