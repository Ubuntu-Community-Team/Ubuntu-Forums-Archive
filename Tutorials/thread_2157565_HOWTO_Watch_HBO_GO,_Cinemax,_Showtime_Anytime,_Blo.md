---
title: "HOWTO Watch HBO GO, Cinemax, Showtime Anytime, Blockbuster and much more on Linux."
date: 2013-06-25
forum: Tutorials
---

### Post by BlackoutWorm on 2013-06-25
Hello. I just want to share with you guys how you can watch a ton of on-demand streaming sites on your linux box.
I'm personally using the wine-browser for this because I've already got Netflix-desktop installed.
You can of course use a fresh Firefox (32 bit) installation as well.
Basically what you need to install inside of firefox is
1) Adobe Flash.
Use the debug installation:
[http://download.macromedia.com/pub/flashplayer/updaters/11/flashplayer_11_plugin_debug.exe](http://download.macromedia.com/pub/flashplayer/updaters/11/flashplayer_11_plugin_debug.exe)
2) Widevine:
[https://tools.google.com/dlpage/widevine](https://tools.google.com/dlpage/widevine)


If you want to use the netflix-desktop method here, simply just copy the /usr/bin/netflix-desktop file, rename it and change the website, app name and icon.
The netflix-desktop app is using bash script, so this pretty easy to understand.


I use gedit to edit these files, btw (gksudo gedit /usr/bin/netflix-desktop).
Here's the netflix-desktop file:
```
#!/bin/sh


# Enable translation capabilities
. gettext.sh
export TEXTDOMAIN="netflix-desktop";
export TEXTDOMAINDIR="/usr/share/locale";
# General strings that are translatable
gettext_service_name=`gettext "Netflix Desktop"`;




WINE_BROWSER="/usr/bin/wine-browser";




PACKAGE="netflix-desktop" SERVICE="${gettext_service_name}" URL="http://www.netflix.com/" "${WINE_BROWSER}" $*;
```


And here's my modified file for HBO Nordic:
```
#!/bin/sh


# Enable translation capabilities
. gettext.sh
export TEXTDOMAIN="hbo-desktop";
export TEXTDOMAINDIR="/usr/share/locale";
# General strings that are translatable
gettext_service_name=`gettext "HBO Desktop"`;




WINE_BROWSER="/usr/bin/wine-browser";




PACKAGE="netflix-desktop" SERVICE="${gettext_service_name}" URL="http://www.hbonordic.com/" "${WINE_BROWSER}" $*;
```


Now for the menu shortcut, located in /home/username/.local/share/applications
Here's the netflix-desktop.desktop file (gedit /home/user/.local/share/applications/netflix-desktop.desktop): 
```
[Desktop Entry]Name=Netflix Desktop
GenericName=Netflix Desktop
Comment=Watch movies and TV shows on your PC
Exec=netflix-desktop
Terminal=false
Type=Application
StartupNotify=true
Icon=/usr/share/icons/netflix.png
Categories=Video;Player;AudioVideo;
```


And my modified file for HBO Nordic:
```



[Desktop Entry]
Name=HBO Nordic Desktop
GenericName=HBO Nordic Desktop
Comment=Watch movies and TV shows on your PC
Exec=hbo-desktop
Terminal=false
Type=Application
StartupNotify=true
Icon=/usr/share/icons/hbo.jpg
Categories=Video;Player;AudioVideo;
Name[nb_NO]=HBO Nordic Desktop
```


And that's how you make apps for your favorite on-demand streaming service.


Now you can watch 100s of on-demand sites such as HBO GO, M GO, MAX GO, SHO Anytime, FilmFresh, Starz/Encore Play, TMC, DishOnline, Blockbuster Movie Pass, Horizon.tv, HBO Nordic.

Btw, here's the PPA for Netflix-Desktop: [https://launchpad.net/netflix-desktop](https://launchpad.net/netflix-desktop)

EDIT: Netflix Desktop is firefox in fullscreen. So to navigate around, you can press CTRL+L.

---

### Post by TechnoJunky on 2013-07-30
I've followed the steps above and have an icon that takes me to HBOGO.com.  HOwever when I get there it says  that I have to have Adobe flash player 10.2 to view HBO Go.  This message seems pretty screwy because I have version 11.8.800.94 installed.  Are they saying I have to have version 10.2 only?  Newer won't cut the mustard?  Any help would be greatly appreciated.

Something odd I just found is that if I use the Netflix desktop and modify it as described above, I get the error about 10.2.  However if I run firefox and browse to HBOGO.com, it works fine, no error and I can watch the videos.

---

### Post by modyl on 2013-09-14
Very cute. Doesn't work, however. 
Vague regarding source of the** HBO Go** shortcut icon.

---

### Post by modyl on 2013-09-14
Very cute. Doesn't work, however. 
Vague regarding source of the HBO Go shortcut icon.

---

### Post by viktor-ulsson on 2013-09-21
It works as a sharm for my HBO Nordic account! Thansk ALOT for this guide, been waiting forever for this to work on Ubuntu.

---

### Post by allen4 on 2013-09-23
How do you install the two files? And widevine is telling me that it doesn't support Linux??? Any help in helping me figure this out would be greatly appreciated!

---

### Post by Askel on 2013-10-07
I can't get flash to work. I tried downloading it and installing it with Wine. But it doesn't work. What am I doing wrong?

//Askel

edit: Nevermind. I went to the adobe flash testsite and installed the flashplugin from there. It just crached when trying to watch videos but I was troubleshooting flash and checking the settings (without actually changing anything and suddenly HBO just worked like a charm. Thanks for this guide. Love to have both HBO and Netflix working. Now I can ditch Windows on this computer.

---

### Post by captainbama29 on 2013-10-14
why don't you just inst  all netflix

To install on Ubuntu / Mint -
Start terminal


$ sudo apt-add-repository ppa:ehoover/compholio


$ sudo apt-get update


$ sudo apt-get install netflix-desktop

and then find the NetFlix Icon under Video click to install and you are done.

---

