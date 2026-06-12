---
title: "Steam works, just not from the Wine menu"
date: 2010-09-24
forum: Wine
---

### Post by Bulletproofmask on 2010-09-24
I recently installed Steam and have found that it runs properly from the command line with Wine.  

Unfortunately, the link under Applications>Wine>Programs>Steam does not yield the same results.  When I try to run Steam from this link I get two error messages: "File not found" and then "There is no Windows program configured to open this type of file".  

I was sure I would be able to find a solution on my own, but a few hours of searching turned up very little.  I am running the latest version of Ubuntu, Wine, Steam.

---

### Post by beastrace91 on 2010-09-24
Wanna post the directory your Steam folder resides as well as the launcher command for the Steam menu entry.

~Jeff

---

### Post by Fableflame on 2010-09-24
Your problem isn't so bad.
I tried to install Steam with WINE and my entire system froze, I had to hard reboot.

---

### Post by Bulletproofmask on 2010-09-24
> **beastrace91 said:**
> Wanna post the directory your Steam folder resides as well as the launcher command for the Steam menu entry.

~Jeff


Steam located at ~/.wine/drive_c/Program\ Files/Steam and the text from the launcher is:

[I][Desktop Entry]
Name=Steam
Exec=env WINEPREFIX="/home/robert/.wine" wine C:\\\\windows\\\\command\\\\start.exe /Unix /home/robert/.wine/dosdevices/c:/users/robert/Start\\ Menu/Programs/Steam/Steam.lnk
Type=Application
StartupNotify=true
Comment=Steam Client
Icon=/home/robert/.local/share/icons/3c3d_icon048298c91.2.png[/I]

---

### Post by Bulletproofmask on 2010-09-24
> **Fableflame said:**
> Your problem isn't so bad.
I tried to install Steam with WINE and my entire system froze, I had to hard reboot.

Ouch

---

### Post by beastrace91 on 2010-09-24
> **Fableflame said:**
> Your problem isn't so bad.
I tried to install Steam with WINE and my entire system froze, I had to hard reboot.

That post is very much borderline spam. Odds are it just froze X. ctrl+alt+f1 would have dropped you to a tty to for an X restart from.

@Bullet Try replacing the command line with this:

**wine /home/robert/.wine/drive_c/Program\ Files/Steam/Steam.exe**

~Jeff

---

### Post by Bulletproofmask on 2010-09-24
That worked perfectly.  I realize now that this was not an issue with Wine and could really have been posted in the Beginners Forum.  Thank you for your help beastrace, I appreciate your time and effort.

---

