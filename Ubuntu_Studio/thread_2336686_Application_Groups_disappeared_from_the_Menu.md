---
title: "Application Groups disappeared from the Menu"
date: 2016-09-10
forum: Ubuntu Studio
---

### Post by javierdl on 2016-09-10
I had the bad idea of adding 2 new applications using MenuLibre. 
As you can see below, MenuLibre does show the Audio Production and Graphic Design sections/folders. Yet they're nowhere in sight in the Ubuntu Studio (US from now on) menu.
Also, even if I enter Gimp in the search bar of the US menu, it won't find it!
What should I do?
I attempted to redo the links to the missing apps, the problem is that I don't know where US installed them. I did a search for Gimp with the folders manager but it only found an addon for Blender. I recalled I had seen a hidden Gimp folder in the root, so I went there. Except I didn't find the actual file that runs the program :(

[IMG]https://sites.google.com/site/javierwebfolio/_/rsrc/1473515420200/temp/MenuLibre.jpg[/IMG]

---

### Post by Dennis N on 2016-09-10
> I attempted to redo the links to the missing apps, the problem is that I don't know where US installed them. I did a search for Gimp with the folders manager but it only found an addon for Blender. I recalled I had seen a hidden Gimp folder in the root, so I went there. Except I didn't find the actual file that runs the program
Your question is where the applications are? User applications installed by apt such as the Menu shows are most likely in /usr/bin or /usr/sbin. Gimp exists in /usr/bin, for example. On this O.S. (not using Ubuntu at the moment), /usr/sbin is just a symbolic link to /usr/bin.

---

### Post by javierdl on 2016-09-10
Gimp is not in my sbin directory :(
I know it's somewhere because I was able to select it and open it when I did a screenshot, I chose to use Gimp to open it.

---

### Post by Dennis N on 2016-09-10
My answer has /usr/bin as the location of Gimp, not /usr/sbin. I checked Xubuntu 16.04 and it is indeed in /usr/bin.

---

### Post by ajgreeny on 2016-09-10
You can usually find the executable for any application with command **which <application-name>** which for gimp produces
```
~$ which gimp
/usr/bin/gimp
```
You do, however, need to know the name of the executable which will be the same as the command used to start the program.

---

### Post by javierdl on 2016-09-10
Dennis, you're right. However, it is not in bin either :(

ajgreeny, thanks, it did find it. And I was able to open it that way. This command will go in my toolset for sure. 
I still wish I could fix that menu though. I wish there was a way to reset it.

---

### Post by javierdl on 2016-09-11
I noticed the Menu was unaffected in the other Ubuntu Studio accounts.
So maybe it's just a matter of copying the files responsible for keeping that information. 
The question now is: Where are those files?
I tried a search but it's not exactly obvious :(

---

### Post by ajgreeny on 2016-09-11
See if you have the file **/usr/share/applications/gimp.desktop** (you should do, I think).

If you can find it open it as root in mousepad, leafpad, gedit, or whatever text-editor you use and find the line **Exec=pathway/to/gimp** and edit it to **Exec=/usr/bin/gimp** or wherever your executable was according to **which gimp**

Or here's a copy of a gimp.desktop file I use which I know works. Copy and save it as a text file called gimp.desktop, put it in the folder /home/*username*/.local/share/applications and after a logout to a new session, or a reboot, you should see the menu item for gimp back in the Graphics section.
```

[Desktop Entry]
Version=1.0
Type=Application
Name=GIMP
GenericName=Image Editor
Comment=Create images and edit photographs
Exec=/usr/bin/gimp
TryExec=gimp-2.8
Icon=gimp
Terminal=false
Categories=Graphics;2DGraphics;RasterGraphics;GTK;
StartupNotify=false

```

---

### Post by javierdl on 2016-09-11
Thanks ajgreeny.
Except that would fix relinking one app only. Whereas I'm missing one whole section in MenuLibre: Graphic Design (which contains Gimp, Krita, etc). Reason why I thought it would be best to go after the files keeping those settings, from the other Ubuntu Studio accounts (I have 3 total). 
Where do you think those file could be?

---

### Post by ajgreeny on 2016-09-12
I prefer **alacarte** for menu edits so it may be worth installing that and looking to see if you can add another section and add your apps to that.  Edits using that seem to have an effect on the whisker menu as well as main menu, if whisker is what ubuntu-studio uses

Menulibre is never quite so easy to deal with in my opinion, but you may disagree after trying it.

---

### Post by javierdl on 2016-09-12
Thanks ajgreeny,
I added back the missing apps, which somehow fixed the Graphic Design section.
I am glad you mentioned Alacarte, I'll keep that in mind for next time.

---

### Post by ajgreeny on 2016-09-12
Great! Please mark as SOLVED, if you are happy that you now have this all sorted, from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

