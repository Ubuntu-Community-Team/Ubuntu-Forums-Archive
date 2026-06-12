---
title: "Tutorial: Unity Launchers and Desktop files"
date: 2012-04-21
forum: Tutorials
---

### Post by hakermania on 2012-04-21
The information in this thread have been moved to [https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

A thread for discussion of the wiki page _only_ can be found here [http://ubuntuforums.org/showthread.php?t=2012385](http://ubuntuforums.org/showthread.php?t=2012385)

Thread closed.

Since the last 3 posts I've helped are mainly about this issue, I see that many users have a problem of making their own launcher, place it to unity, edit a launcher of unity etc.

This tutorial will show all the basics you need to know on how to have your unity launcher as you want and how to create desktop files for this or other purpose.[B]

[SIZE=3]          1.   How to create a .desktop file[/SIZE][/B]

.desktop files are files for launching links or applications (here I cover applications).
To create one, you can use gedit to manually create a desktop file or install a program for it. Both ways are easy but with the former you have more control on launcher's behavior

**a) Use gedit**

Open gedit and paste in:
```
[Desktop Entry]
Version=1.6
Name=ProgramName
Comment=My comment is this
Exec=/home/alex/Documents/exec.sh
Icon=/home/alex/Pictures/icon.png
Terminal=false
Type=Application
Categories=Utility;Application;

```
Edit all the fields except 'Type' and 'Terminal' probably, so as to much your needs. 'Categories' field should be OK to be left as is, if you are working on a script or something similar.

A realistic example is the following:
```
[Desktop Entry]
Version=2.3
Name=Wallch
Comment=Change wallpapers automatically
Exec=/usr/bin/wallch
Icon=/usr/share/icons/wallch.png
Terminal=false
Type=Application
Categories=Utility;Application;

```

You can now do right click on your file->Properties->Permissions->Allow executing file as program and use your launcher with double click! This action will change the .desktop's file look.
Specifically, it will hide the .desktop extension, it will rename it to what the field 'Name' inside the .desktop file has, and, finally, it will show the icon!
Launcher without execution permissions:
[CENTER][IMG]http://i.imgur.com/zkVoi.png[/IMG]
[LEFT]Launcher with execution permissions:
[CENTER][IMG]http://i.imgur.com/2W7KG.png[/IMG]

[LEFT]Please note that in reality _the filename is still the same_**, **just the system chooses to show it like this because it's nicer.
[/LEFT]
[/CENTER]
[/LEFT]
[/CENTER]
 1->a
**b) Use gnome-desktop-item-edit**

This way is simpler.
Run the following command:
```

sudo apt-get install --no-install-recommends gnome-panel

```
and then
```

gnome-desktop-item-edit ~/.local/share/applications/ --create-new

```
where ~/.local/share/applications/ could be any other output path you want the launcher to appear, like ~/Desktop/
After you run this command, a window will appear which will let you choose the launcher's options. Also, note that by clicking on the icon on the top left of the window which opened you can choose an icon for your launcher.

After pressing OK, the launcher will be placed where you specified throough the command line (the 1st argument after the command gnome-desktop-item-edit)


**[SIZE=3]          2.   Have your .desktop file appear in Unity launcher[/SIZE]**

In order to add your launcher to the Unity bar on the left, you have to place your launcher at /usr/share/applications/ or at ~/.local/share/applications/ (the former needs root permission while the latter no, but the former has not problems at all while the latter has showed some problems at me, like it doesn't show the program's name or similar).
After moving your file there, search for it in Dash (Windows key -> type the name of the application) and drag en drop it to the unity bar. Now your launcher is on the unity bar!


**[SIZE=3]          3.   How to edit a launcher of the Unity bar[/SIZE]**

**a) Edit its main characteristics**
First of all, you need to know the exact name of the launcher, not the name of the program it launches. For this purpose, open a terminal (Ctrl+Alt+T) and give this command:
```

gsettings get com.canonical.Unity.Launcher favorites

```
It will show you a list of the names of all the launchers you have in your unity launcher, starting from the top of the unity launcher and going to the bottom o f it.
Now, you can detect the name of the launcher you want to edit. Copy it to clipboard (select it->right click->copy) for later use.
In a terminal head to /usr/share/applications:
```

cd /usr/share/applications

```
and edit the launcher that is placed there (remember that you have its name in your clilpboard) using the command:
```

gksudo gedit [paste here what you have in your clipboard with right click->paste or Ctrl+Shift+V]

```
It will ask you for password. Type in your login password and gedit will open with the launcher file you wish to edit. To edit the launcher go to **1->a** of this tutorial on the top, where it says it clearly on how to create a launcher and the same applies on editing it.

**b) Add shortcuts to a launcher**

After adding the main characteristics of a launcher, such as filling its 'Name' and 'Exec' fields, then you can add one or more shortcuts like these:
[CENTER][IMG]http://i.imgur.com/AyRia.png[/IMG]

[LEFT]An example of adding these shortcuts is the best way to learn how to do it, as it's very simple.
This is a working .desktop file for Audacious, an awesome music player which provides its launcher with the shortcuts 'Play', 'Pause', 'Next' and 'Previous' and they do the corresponding action:
```

[Desktop Entry]
Version=1.0

Type=Application

Name=Audacious
GenericName=Music Player
GenericName[be]=&#1052;&#1091;&#1079;&#1099;&#1095;&#1085;&#1099; &#1087;&#1083;&#1101;&#1077;&#1088;
GenericName[da]=Lydafspiller
GenericName[de]=Musikspieler
GenericName[es]=Reproductor de música
GenericName[fr]=Lecteur de Musique
GenericName[it]=Lettore di Musica
GenericName[lt]=Muzikos grotuvas
GenericName[nl]=Muziekspeler
GenericName[nb]=Lydavspiller
GenericName[pt]=Leitor de Música
GenericName[ro]=Lector de Muzic&#259;
GenericName[ru]=&#1040;&#1091;&#1076;&#1080;&#1086;&#1087;&#1083;&#1077;&#1077;&#1088;
GenericName[se]=Ljudspelare
Comment=Listen to music
Comment[be]=&#1057;&#1083;&#1091;&#1093;&#1072;&#1081;&#1094;&#1077; &#1084;&#1091;&#1079;&#1099;&#1082;&#1091;
Comment[de]=Musik hören
Comment[fr]=Écouter de la musique
Comment[hu]=Hallgasson zenét
Comment[it]=Ascoltare musica
Comment[lt]=Klausyti muzikos
Comment[nb]=Lytt til musikk
Comment[nl]=Muziek luisteren
Comment[ru]=&#1057;&#1083;&#1091;&#1096;&#1072;&#1081;&#1090;&#1077; &#1084;&#1091;&#1079;&#1099;&#1082;&#1091;
Comment[es]=Escucha música
Icon=audacious

Categories=AudioVideo;Audio;Player;GTK;

Exec=audacious %U
TryExec=audacious
Terminal=false
MimeType=application/ogg;application/x-cue;application/x-ogg;application/xspf+xml;audio/midi;audio/mp3;audio/mpeg;audio/mpegurl;audio/ogg;audio/prs.sid;audio/x-flac;audio/x-it;audio/x-mod;audio/x-mp3;audio/x-mpeg;audio/x-mpegurl;audio/x-ms-wma;audio/x-musepack;audio/x-s3m;audio/x-scpls;audio/x-stm;audio/x-vorbis+ogg;audio/x-wav;audio/x-xm;x-content/audio-cdda;

X-Ayatana-Desktop-Shortcuts=Play;Pause;Next;Previous;

[Play Shortcut Group]
Name=Play
Exec=audacious -p
TargetEnvironment=Unity

[Pause Shortcut Group]
Name=Pause
Exec=audacious -t
TargetEnvironment=Unity

[Next Shortcut Group]
Name=Next
Exec=audacious -f
TargetEnvironment=Unity

[Previous Shortcut Group]
Name=Previous
Exec=audacious -r
TargetEnvironment=Unity

```
The thing that has to do with shortcuts is everything _after_ '**X-Ayatana-Desktop-Shortcuts=Play;Pause;Next;Previous;**' including this.
Through the manpage of audacious I very easily found how to go to the Next/Previous song and Pause/Play it, so it was very easy to add some shortcuts.
Please note that an application can have 'live' shortcuts that change during the program's execution, but that's another story, not directly linked to the contents of the .desktop file of the application!



That's all, if you have any comments or additions please add them.
[/LEFT]
[/CENTER]

---

### Post by mc4man on 2012-04-24
A few comments on, mainly concerning custom .desktops

If there is any use possible or desired for DnD on the launcher than a MimeType= line needs to be present with appropriate types listed.

The Categories= will & can be used to affect where the launcher will appear in the Dash apps menu > Filter results

When a custom .desktop is created & desired to show on the right click context menu the Exec= line needs to end with a %<letter>, typically %U, %f or %F

Regarding quicklists - starting in **12.04** it has been moved to Desktop Actions though 12.04 will still allow "X-Ayatana-Desktop-Shortcuts"
The new way would be to use instead - using the audacious as EX.

Actions=Play;Pause;Next;Previous;

[Desktop Action Play]
Name=Play
Exec=audacious -p
TargetEnvironment=Unity

Ect.

The order that  quicklists are displayed in the launcher is solely determined by the order listed in the X-Ayatana-Desktop-Shortcuts= or Actions= line. This line also determines what quicklists are shown, you can remove a quicklist option by removing it's entry in that line, the section can remain in case you want to add back at some point

Of minor interest thru 12.04.
Some apps may be better without the global menu, this can be changed thru it's .desktop for most uses (doesn't affect when starting from rhe terminal

For most apps this will do, added to the Exec= line, not used in quicklists unless the quicklist is launching a new instance. Ex. again of audacious

```
Exec=env UBUNTU_MENUPROXY=0 audacious %U
```

For qt4 apps a different env, example vlc
```
Exec=env QT_X11_NO_NATIVE_MENUBAR=1 vlc %U
```

---

### Post by hakermania on 2012-04-29
Thanks for the additions! Interesting facts :)

---

### Post by Elfy on 2012-06-29
This thread is closed. 
 
The information is now held on the community wiki at [https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)
 
Thank you for your thread and the work you have done in keeping it current and of use to the community. 
 
A thread for discussion of the wiki can be found at [http://ubuntuforums.org/showthread.php?t=2012385](http://ubuntuforums.org/showthread.php?t=2012385) 
 
Support threads regarding the wiki and it's content should be created in a suitable forum.

---

