---
title: "Warcraft III (Frozen Throne) PROBLEMS"
date: 2009-12-05
forum: Wine
---

### Post by Taeyeon on 2009-12-05
Terribly sorry, I'm a complete noob to Linux and everything it includes
I just downloaded Wine's new version etc. etc.
And when I try to run Frozen Throne it starts working in the beginning but then 
the whole screen turns either white or black. And to the extent of my knowledge
the only way I am currently able to get out of it is by restarting my computer...
Am I doing something wrong or is my computer being stupid?
Thanks, and don't hate on me if I posted something wrong somehow >_<

Oh yeah, and I'm running Warcraft III off a USB...

---

### Post by PandaGoat on 2009-12-06
In the installation directory of Warcraft III, delete or rename the Movies folder.  Also, be sure to run it with -opengl at the end: WINEDEBUG=-all wine war3.exe -opengl

I believe you have to compile the newest wine with some patches to get some features like hosting to work.  I can help you do this.  If you already know what I'm talking about refer to my Arch Linux package for wine patched to play Warcraft that has the list of patches: [http://aur.archlinux.org/packages.php?ID=27298](http://aur.archlinux.org/packages.php?ID=27298)

---

### Post by Judy-Pond-FTL on 2009-12-06
> **PandaGoat said:**
> In the installation directory of Warcraft III, delete or rename the Movies folder.  Also, be sure to run it with -opengl at the end: WINEDEBUG=-all wine war3.exe -opengl

I believe you have to compile the newest wine with some patches to get some features like hosting to work.  I can help you do this.  If you already know what I'm talking about refer to my Arch Linux package for wine patched to play Warcraft that has the list of patches: [http://aur.archlinux.org/packages.php?ID=27298](http://aur.archlinux.org/packages.php?ID=27298)



For some reason when I go to the Warcraft III folder it isn't possible to "Rename folder" or "Delete Folder"...

---

### Post by yanom on 2009-12-06
> 
For some reason when I go to the Warcraft III folder it isn't possible to "Rename folder" or "Delete Folder"...
possibly you don't have the right file permissions (you aren't administrator). Do it from the command line:

```

su
cd <directory_where_Warcraft_III_is_installed>
mv ./Movies ./Moviez

```

note that after typing "su" you will have to type in your password. The characters won't show up on the screen (security feature), just type it in and hit enter/return.

---

