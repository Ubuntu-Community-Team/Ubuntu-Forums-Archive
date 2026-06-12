---
title: "XFCE Menu-Panel give me an error"
date: 2012-12-14
forum: Ubuntu Studio
---

### Post by akimb0 on 2012-12-14
Hello,

got a strange problem with my ubuntustudio 12.10 quantal release.

I was thinking about to disable some icons from the menu which can be opened from the very left top side of the desktop and started to edit these icons with the GUI given by xfce (dont blame me about the name, i dont remember it).

After disabling some icons the complete panel was gone and shows me an error (see later). The menupanel is still active but im not longer able to open it from the left top side. I got an error message that my desktop is unable to load the menu. 

Here is what  ~.xsession-errors say: ```
** (xfdesktop:2889): WARNING **: Unable to load menu: Fehler in Zeile 1, Zeichen 1: Dokument ist leer oder enthält nur Leerraum
```Sorry for the german logs, ill try to translate it: ```
** (xfdesktop:2889): WARNING **: Unable to load menu: Error in Line 1, Sign 1: Document seems to be empty or it only contains empty space
```renaming the ~.config/xfce4 doesnt help

Any ideas?

---

### Post by akimb0 on 2012-12-16
I checked on my laptop what kind of editor i used to disable some menuentrys. It was the original XFCE4 menueditor which can be reached through the menu->properties->menueditor (in german its named Einstellungseditor)

Here you can enable or disable menuentrys the graphical way, which i did. As i saved the settings the menu was gone with the error message i described i my first post.

No one got a light for me?

---

### Post by akimb0 on 2012-12-21
Got it...
If theres anyone outside who have the same problem, heres what i did to get it running.


I looked in ~.config/menus and compared the files here on my dekstop and my laptop. 


I saw that my desktop (which give me that error described before) got a file named xfce-applications.menu. 
On my laptop, which of course also runs ubuntu-studio, i dont had that file.



I deleted the xfce-applications.menu from my desktop and after that my menu was back again included all entrys.
[SOLVED]

---

