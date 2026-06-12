---
title: "How to reset app to default"
date: 2021-07-08
forum: Ubuntu/Debian BASED
---

### Post by david1992 on 2021-07-08
I use Zorin OS which is based on UBuntu. Please answer me how to reset an app to default, for instance VLC player?

---

### Post by TheFu on 2021-07-08
Configurations are stored per-userid, in the user's HOME directory (somewhere).  I'd look under ~/.config/vlc/.  Delete everything below that.
If that doesn't work, like with Gnome apps, the settings/configurations could be stored in a per-userid database file. Unfortunately, Gnome has decided that having 1 file shared for all programs is a good idea (it isn't), so we can hunt through the DB looking for application specific settings to remove (looking inside a DB file isn't as easy as using an editor, IMHO)
or
just create a new userid and start using that instead. Doing this will reset all settings to the default for the new userid.

---

### Post by coffeecat on 2021-07-08
Zorin. *Thread moved to **Ubuntu/Debian Based** sub-forum.*

---

### Post by david1992 on 2021-07-10
> **TheFu said:**
> Configurations are stored per-userid, in the user's HOME directory (somewhere).  I'd look under ~/.config/vlc/. 
Please help me wher to find configuration file. In which folder configuration file is placed



[img]https://i.imgur.com/5KdYKbS.png[/img]
[img]https://i.imgur.com/Vak2iIB.png[/img]

---

### Post by TheFu on 2021-07-11
a) please don't post huge images.
b) Did you put "~/.config/vlc/" into the URL entry and hit enter?

---

### Post by david1992 on 2021-07-11
Solved. I found the folder and delete data:

---

### Post by TheFu on 2021-07-11
snap packages are new.  I avoid them for a number of reasons.

Please don't post images. Make them attachments for the people who have to pay for internet by the byte. Be kind.

---

