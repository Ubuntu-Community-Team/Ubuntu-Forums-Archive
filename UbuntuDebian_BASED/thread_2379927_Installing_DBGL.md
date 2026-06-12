---
title: "Installing DBGL"
date: 2017-12-11
forum: Ubuntu/Debian BASED
---

### Post by lightbearer972 on 2017-12-11
Hello,

I've dabbled in Linux on and off for the past several years, and I may be getting to the point where I am ready to switch to Linux as my daily driver. I'm relatively knowledgeable about installing software from a graphical package manager such as a software center, but installing things from a command line still gives me trouble from time to time.

Case in point: I am an avid retro gamer and use DOSBox a lot. I've been wanting to try DBGL (a graphical frontend for DOSBox) to make organizing my library easier, but it doesn't seem to be too easy to install. Specifically, you have to download it manually and launch it using a terminal.

I'm running Pop_OS and have installed DOSBox from its software center. Can somebody walk me through putting DBGL in an appropriate folder, linking it to my current DOSBox install, and creating an icon for it in GNOME's list of installed apps?

The home page is [here]("http://members.quicknet.nl/blankendaalr/dbgl/")

Thanks for helping a newbie out.

Luke

---

### Post by Holger_Gehrke on 2017-12-11
It's actually very simple.[INDENT]1. Install a JRE (Java Runtime Environment). You'll need it since dbgl is written in java. (I already had OpenJDK 8 installed, so I didn't need to do that; if you can't find it in the software center, try 'sudo apt-get install openjdk-8-jre' in a terminal)
[/INDENT]
[INDENT]2. Make a directory somewhere in your home directory and unpack the archive there (you can cut and paste this; everything after the '#' is recognized by the shell as comment; paste into terminal windows is shift-ctrl-v, ctrl-v has a different meaning in the terminal): 
[/INDENT]
 ```

mkdir ~/dbgl # make the directory
cd ~/dbgl # make the new directory your working directory
tar -xzf[COLOR=#ff0000] ~/Downloads/dbgl082_generic.tar.gz[/COLOR] # unpack the archive; change the path and file name to the directory and file name of your downloaded dbgl
nano dbgl.desktop # open an editor to create a .desktop-file for dbgl
```[INDENT]3. Paste the following into the editor: 
[/INDENT]
 ```

[Desktop Entry]
Version=1.0
Type=Application
Name=DBGL
Comment=DOS-Box Game Launcher
Icon=/home/[COLOR=#ff0000]<username>[/COLOR]/[COLOR=#000000]dbgl/dbgl.png[/COLOR]
Exec=/home/[COLOR=#ff0000]<username>[/COLOR]/dbgl/dbgl
Path=/home/[COLOR=#ff0000]<username>[/COLOR]/dbgl/
NoDisplay=false
Categories=Game
StartupNotify=true
Terminal=false

``` replace [COLOR=#ff0000]<username>[/COLOR] with your username, save with ctrl-o and exit with ctrl-x.[INDENT]4. Move the dbgl.desktop file to ~/.local/share/applications/ 
[/INDENT]
```
mv dbgl.desktop ~/.local/share/applications/
``` and we should be done done. If System76 set gnome in Pop!_OS up the same way it is set up in Ubuntu, then whatever launcher or menu-system you're using should pick up the .desktop file and give you an Icon for dbgl. Everything else is close to automatic. If you have dosbox installed, then dbgl will pick it and its configuration up automatically. 

Holger

---

### Post by deadflowr on 2017-12-11
*Thread moved to **Ubuntu/Debian BASED***

---

