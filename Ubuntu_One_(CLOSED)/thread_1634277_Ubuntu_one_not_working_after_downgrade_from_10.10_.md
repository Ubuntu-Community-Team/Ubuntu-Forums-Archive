---
title: "Ubuntu one not working after downgrade from 10.10 to 10.04"
date: 2010-11-30
forum: Ubuntu One (CLOSED)
---

### Post by djpemberton on 2010-11-30
After having too many frustrations on my computers with 10.10 I moved back to 10.04, which relieved nearly all of my frustrations. My Home directory was on a separate partition which I retained during the downgrade. Everything seems to be working perfectly except Ubuntu One. "Ubuntu One Preferences" lists my Name, E-mail, Current plan, and progress as "Unknown" and will not sync. It remains like this even after adding my computer to the account again and completely uninstalling and reinstalling Ubuntu One. Does anyone know any way to fix this?

---

### Post by duanedesign on 2010-11-30
This is likely caused by incompatible metadata between versions.
To fix this you need to repopulate your metadata with the version currently in use by your version of Ubuntu One. If you have anything of great importance in your Ubuntu One folder you you might want to back it up before proceeding (never can be too safe)

1. Quit the Ubuntu One client. From the applet select Quit. Then open a Terminal (Applications > Accessories > Terminal) and run the following to quit the syncdaemon.

u1sdtool -q

2. Delete the old metadata. In a Terminal run.

rm -rf ~/.local/share/ubuntuone

3. Start Ubuntu One as you normally would Me Menu --> Ubuntu One or System --> Preferences --> Ubuntu One

It'll run for a bit as it recreates the metadata.

---

