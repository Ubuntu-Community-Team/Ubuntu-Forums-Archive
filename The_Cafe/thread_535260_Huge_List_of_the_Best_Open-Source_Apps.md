---
title: "Huge List of the Best Open-Source Apps"
date: 2007-08-26
forum: The Cafe
---

### Post by TheWiseNoob on 2007-08-26
[CENTER][size=10][color=#deb086]Top 100 Open-Source Linux Apps[/color][/size]


Currently at  [FONT="Arial Black"][SIZE="2"]92/100[/SIZE][/FONT]  apps[/center]


[color=#cbc8a9][b]Once it hits 100, only apps much better than others listed will be put on the list and the least popular will be removed.

I made this list because I realized how long it took, for me, to discover even a small portion of these apps when I first started using Linux. Hopefully someone new to Linux or looking for programs they have never used finds this helpful.

The "Installation" part of this list is currently incomplete. All of the application names lead to its project site.  Posting how to install one of these programs, another program you think should be on this list, a revision I should make to the organization of the list, or notifying me of any mistake/broken link on the list would help me a lot. I will be constantly updating this. Enjoy![/b][/color]



[color=#808080][size=5]**BitTorrent Clients**[/color][/size]



[INDENT][[color=#bd5900][size=4]**Azureus**[/color][/size]](http://azureus.sourceforge.net/)
Java-based BitTorrent client for both beginners and advanced users. There as features included, such as, multiple torrent downloads, advanced seeding rules, pausing a torrent, importing torrents, and much, much more.

[color=#a9a9a9][size=2]**INSTALLATION**[/color][/size]

Open Synaptic Package Manager and serach for "azureus". Mark the program named "azureus" for installation. Click apply. 

[[color=#bd5900][size=1]**~Visit Site~**[/color][/size]](http://azureus.sourceforge.net/)


[[color=#bd5900][size=4]**Deluge**[/color][/size]](http://deluge-torrent.org/downloads)
A very lightweight, BitTorrent client using GTK and python. It is one of the most rapidly developing clients and is very comparable to µTorrent. Integrates well with the GNOME desktop environment.

[color=#a9a9a9][size=2]**INSTALLATION**[/color][/size]

Open Synaptic Package Manager and serach for "deluge-torrent". Mark the program named "deluge-torrent" for installation. Click apply. 

[[color=#bd5900][size=1]**~Visit Site~**[/color][/size]](http://deluge-torrent.org/downloads)


[[color=#bd5900][size=4]**KTorrent**[/color][/size]](http://ktorrent.org/)
A BitTorrent client for KDE. It is very lightweight and has many of the features that most BitTorrent clients include. Though it is still missing many key features, is under heavy development.

[color=#a9a9a9][size=2]**INSTALLATION**[/color][/size]

Open Synaptic Package Manager and serach for "ktorrent". Mark the program named "ktorrent" for installation. Click apply. 

[[color=#bd5900][size=1]**~Visit Site~**[/color][/size]](http://ktorrent.org/)


[[color=#bd5900][size=4]**rTorrent**[/color][/size]](http://libtorrent.rakshasa.no/)[/INDENT]





[color=#808080][size=5]**EyeCandy**[/color][/size]



[INDENT][[color=#bd5900][size=4]**Avant Window Navigator(AWN)**[/color][/size]](http://code.google.com/p/avant-window-navigator/)
A dock-like bar which sits at the bottom of the screen tracking open windows. It requires a compositor to be running, or it will not display properly. Has stcks feature, like in Mac OS X 10.5 Leopard.

[color=#a9a9a9][size=2]**INSTALLATION**[/color][/size]

[list=1]
[*]First, open terminal so you can edit your sources.list:
```
sudo gedit /etc/apt/sources.list
```
and add these two lines:
```
deb http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator
```



[*]Now enter:
```
wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg -O- | sudo apt-key add -
```
```
sudo apt-get update
sudo apt-get upgrade
```



[*]To install AWN, enter:
```
sudo apt-get install avant-window-navigator-bzr
```
[/list]

[[color=#bd5900][size=1]**~Visit Site~**[/color][/size]](http://code.google.com/p/avant-window-navigator/)


[[color=#bd5900][size=4]**Compiz Fusion**[/color][/size]](http://compiz.org/)
A compositing window managers for the X Window System that is able to take advantage of OpenGL acceleration. The integration allows it to perform compositing effects in window management, such as a minimization effect and a cube workspace. It was created from the remerging of Beryl into Compiz.

[color=#a9a9a9][size=2]**INSTALLATION**[/color][/size]

[list=1]
[*]  Enter this first:
```
sudo apt-get -y remove compiz-core desktop-effects
```
This will remove any older/broken installs of Compiz Fusion.



[*]  If you are using Gutsy, skip to step 4. Do this to edit your sources.list:
```
sudo gedit /etc/apt/sources.list
```
and add these two lines:
```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```
You can now close Gedit.



[*]  Next, enter this:
```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg
```
Then this:
```
sudo apt-key add DD800CD9.gpg
```
```
sudo apt-get upgrade
```



[*]  Now enter this to install to install Compiz Fusion:
```
sudo apt-get -y install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
```



[*]  To start Compiz Fusion, enter this in Terminal or Run:
```
compiz --replace
```
You can edit Compiz Fusion settings by going to System -- Preferences -- Compiz Config Settings Manager .

[/list]

[[color=#bd5900][size=1]**~Visit Site~**[/color][/size]](http://compiz.org/)


[[color=#bd5900][size=4]**Emerald**[/color][/size]](http://www.beryl-project.org/)
A window decorator for Compiz Fusion and Beryl. A much more extensive decorator than Metacity.

[color=#a9a9a9][size=2]**INSTALLATION**[/color][/size]

Open Synaptic Package Manager and serach for "emerald". Mark the program named "emerald" for installation. Click apply. 

[[color=#bd5900][size=1]**~Visit Site~**[/color][/size]](http://www.beryl-project.org/)


[[color=#bd5900][size=4]**gDesklets**[/color][/size]](http://www.gdesklets.de/)
Tiny applets that sit on your desktop in a symbiotic relationship of eye candy and usefulness. You can populate your desktop with status meters, icon bars,weather sensors, news tickers, and whatever else you can imagine. gDesklets does not require a compositor to work correctly.

[color=#a9a9a9][size=2]**INSTALLATION**[/color][/size]

Open Synaptic Package Manager and serach for "gdesklets". Mark the program named "gdesklets" for installation. Click apply.

[[color=#bd5900][size=1]**~Visit Site~**[/color][/size]](http://www.gdesklets.de/)


[[color=#bd5900][size=4]**Screenlets**[/color][/size]](http://screenlets.org/index.php/Home)
Screenlets are small, owner-drawn applications written in Python. They are a form of eyecandy that are easy to create and can be used as Widgets. They help create a Mac-Like Desktop Environment.

[color=#a9a9a9][size=2]**INSTALLATION**[/color][/size]

[list=1]
[*]This application requires you to have a compositor, like Compiz Fusion or Beryl, for it to work properly. 
Download the latest screenlets source from the [[color=#bd5900][size=1]**Screenlets Download Page**[/color][/size]](http://screenlets.org/index.php/Download). Extract the folder, in the archive, to your Desktop and rename it to screenlets.



[*]Open terminal and enter:
```
cd Desktop/screenlets
```



[*]Then enter:
```
sudo make install
```
Screenlets is now installed.



[*]To install the menu items, using the same terminal window, enter:
```
 sudo make menu
```
The menu items are now installed and there should be a "Screenlets" directory in you Applications Menu now.
You must start each screenlet individually. There are 3rd-party screenlets located at the [[color=#bd5900][size=1]**Screenlets Download Page**[/color][/size]](http://screenlets.org/index.php/Download).


[/list][[color=#bd5900][size=1]**~Visit Site~**[/color][/size]](http://screenlets.org/index.php/Home)[/INDENT]






[color=#808080][size=5]**File Browser/Search**[/color][/size]



[INDENT][[color=#bd5900][size=4]**Affinity**[/color][/size]](http://code.google.com/p/affinity-search/)


[[color=#bd5900][size=4]**Appfinder**[/color][/size]](http://www.xfce.org/projects/xfce4-appfinder)
An application finder for the GNOME or Xfce4 Desktop Environment. It will search for installed applications on your system.

[color=#a9a9a9][size=2]**INSTALLATION**[/color][/size]

Open Synaptic Package Manager and serach for "xfce4-appfinder". Mark the program named "xfce4-appfinder" for installation. Click apply.

[[color=#bd5900][size=1]**~Visit Site~**[/color][/size]](http://www.xfce.org/projects/xfce4-appfinder)


[[color=#bd5900][size=4]**Beagle**[/color][/size]](http://beagle-project.org/Main_Page)
A desktop search utility for indexing and searching user's data. At the moment, it can index filesystems, Pidgin logs, Evolution data, RSS and many more.

[color=#a9a9a9][size=2]**INSTALLATION**[/color][/size]

Open Synaptic Package Manager and serach for "beagle". Mark the program named "beagle" for installation. Click apply.

[[color=#bd5900][size=1]**~Visit Site~**[/color][/size]](http://beagle-project.org/Main_Page)


[[color=#bd5900][size=4]**Nautilus**[/color][/size]](http://www.gnome.org/projects/nautilus/)
The official file manager for the GNOME desktop. It allows to browse directories, preview files and launch applications associated with them. It is also responsible for handling the icons on the GNOME desktop. It works on local and remote filesystems.

[color=#a9a9a9][size=2]**INSTALLATION**[/color][/size]

Installed by default on Ubuntu. The source can be found [[color=#bd5900][size=1]**here**[/color][/size]](http://ftp.gnome.org/pub/gnome/sources/nautilus/2.12/nautilus-2.12.0.tar.gz).

[[color=#bd5900][size=1]**~Visit Site~**[/color][/size]](http://www.gnome.org/projects/nautilus/)


[[color=#bd5900][size=4]**Thunar**[/color][/size]](http://thunar.xfce.org/index.html)
The file manager designed to be the default file manager of Xfce 4.4 It has been designed to be fast and easy to use.

[color=#a9a9a9][size=2]**INSTALLATION**[/color][/size]

Open Synaptic Package Manager and serach for "thunar". Mark the program named "thunar" for installation. Click apply.

[[color=#bd5900][size=1]**~Visit Site~**[/color][/size]](http://thunar.xfce.org/index.html)[/INDENT]






[color=#808080][size=5]**Games**[/color][/size]



[Indent][[color=#bd5900][size=4]**Alien Arena 2007**[/color][/size]](http://red.planetarena.org/)

[color=#a9a9a9][size=2]**INSTALLATION**[/color][/size]

Open Synaptic Package Manager and serach for "alien-arena". Mark the program named "alien-arena" for installation. Click apply.

[[color=#bd5900][size=1]**~Visit Site~**[/color][/size]](http://red.planetarena.org/)

[[color=#bd5900][size=4]**Battle for Wesnoth**[/color][/size]](http://www.wesnoth.org/)


[[color=#bd5900][size=4]**Frets On Fire**[/color][/size]](http://fretsonfire.sourceforge.net/)


[[color=#bd5900][size=4]**Neverball**[/color][/size]](http://icculus.org/neverball/)


[[color=#bd5900][size=4]**Nexuiz**[/color][/size]](http://alientrap.org/nexuiz/)


[[color=#bd5900][size=4]**Open Arena**[/color][/size]](http://openarena.ws/?)


[[color=#bd5900][size=4]**Sauerbraten**[/color][/size]](http://sauerbraten.org/)


[[color=#bd5900][size=4]**Stepmania**[/color][/size]](http://stepmania.com)


[[color=#bd5900][size=4]**Scorched 3D**[/color][/size]](http://www.scorched3d.co.uk/)


[[color=#bd5900][size=4]**Tremulous**[/color][/size]](http://www.tremulous.net/)[/INDENT]






[color=#808080][size=5]**Graphics and Text Viewers/Editors**[/color][/size]



[INDENT][[color=#bd5900][size=4]**Amaya**[/color][/size]](http://www.w3.org/Amaya/)


[[color=#bd5900][size=4]**Abiword**[/color][/size]](http://www.abisource.com/)


[[color=#bd5900][size=4]**Blender**[/color][/size]](http://www.blender.org/)


[[color=#bd5900][size=4]**Bluefish**[/color][/size]](http://bluefish.openoffice.nl/)


[[color=#bd5900][size=4]**F-Spot**[/color][/size]](http://f-spot.org/Main_Page)


[[color=#bd5900][size=4]**Gedit**[/color][/size]](http://www.gnome.org/projects/gedit/)


[[color=#bd5900][size=4]**The GIMP**[/color][/size]](http://www.gimp.org/)


[[color=#bd5900][size=4]**Gnumeric Spreadsheet**[/color][/size]](http://www.gnome.org/projects/gnumeric/)


[[color=#bd5900][size=4]**GNU Paint**[/color][/size]](http://gpaint.sourceforge.net/)


[[color=#bd5900][size=4]**Inkscape**[/color][/size]](http://www.inkscape.org/)


[[color=#bd5900][size=4]**Kolourpaint**[/color][/size]](http://kolourpaint.sourceforge.net/)


[[color=#bd5900][size=4]**OpenOffice.org**[/color][/size]](http://openoffice.org)


[[color=#bd5900][size=4]**Scribus**[/color][/size]](http://www.scribus.net/)


[[color=#bd5900][size=4]**Zim Desktop Wiki**[/color][/size]](http://pardus-larus.student.utwente.nl/~pardus/projects/zim/)[/INDENT]






[color=#808080][size=5]**Music and Video Players**[/color][/size]



[INDENT][[color=#bd5900][size=4]**Amarok**[/color][/size]](http://amarok.kde.org/)


[[color=#bd5900][size=4]**Audacious**[/color][/size]](http://audacious-media-player.org/Main_Page)


[[color=#bd5900][size=4]**Banshee**[/color][/size]](http://banshee-project.org/Main_Page)


[[color=#bd5900][size=4]**Cheese**[/color][/size]](http://live.gnome.org/Cheese)


[[color=#bd5900][size=4]**Totem**[/color][/size]](http://www.gnome.org/projects/totem/)


[[color=#bd5900][size=4]**Exaile**[/color][/size]](http://exaile.org/)


[[color=#bd5900][size=4]**gmusicbrowser**[/color][/size]](http://squentin.free.fr/gmusicbrowser/gmusicbrowser.html)


[[color=#bd5900][size=4]**Kaffeine**[/color][/size]](http://hftom.free.fr/)


[[color=#bd5900][size=4]**Listen**[/color][/size]](http://www.listen-project.org/)


[[color=#bd5900][size=4]**Miro**[/color][/size]](http://www.getmiro.com/)


[[color=#bd5900][size=4]**MythTV**[/color][/size]](http://mythtv.org/)


[[color=#bd5900][size=4]**Rhythmbox**[/color][/size]](http://www.gnome.org/projects/rhythmbox/)


[[color=#bd5900][size=4]**Songbird**[/color][/size]](http://www.songbirdnest.com/)


[[color=#bd5900][size=4]**VideoLAN Client(VLC)**[/color][/size]](http://www.videolan.org/)


[[color=#bd5900][size=4]**XMMS2**[/color][/size]](http://wiki.xmms2.xmms.se/index.php/Main_Page)[/INDENT]






[color=#808080][size=5]**Network Programs**[/color][/size]



[INDENT][[color=#bd5900][size=4]**aKregator**[/color][/size]](http://akregator.kde.org/)


[[color=#bd5900][size=4]**Ekiga VoIP**[/color][/size]](http://ekiga.org/)


[[color=#bd5900][size=4]**Evolution**[/color][/size]](http://www.gnome.org/projects/evolution/)


[[color=#bd5900][size=4]**FileZilla**[/color][/size]](http://filezilla.sourceforge.net/)


[[color=#bd5900][size=4]**gFTP**[/color][/size]](http://gftp.seul.org/)


[[color=#bd5900][size=4]**irssi**[/color][/size]](http://irssi.org/)


[[color=#bd5900][size=4]**Kopete**[/color][/size]](http://kopete.kde.org/)


[[color=#bd5900][size=4]**Mumble**[/color][/size]](http://mumble.sourceforge.net/)


[[color=#bd5900][size=4]**Pidgin**[/color][/size]](http://pidgin.im)


[[color=#bd5900][size=4]**Straw**[/color][/size]](http://www.gnome.org/projects/straw/)


[[color=#bd5900][size=4]**Thunderbird**[/color][/size]](http://www.mozilla.com/en-US/thunderbird/)


[[color=#bd5900][size=4]**XChat**[/color][/size]](http://www.xchat.org/)[/INDENT]






[color=#808080][size=5]**Programming IDEs**[/color][/size]



[INDENT][[color=#bd5900][size=4]**Anjuta**[/color][/size]](http://anjuta.sourceforge.net/)


[[color=#bd5900][size=4]**Code::Blocks**[/color][/size]](http://www.codeblocks.org/)


[[color=#bd5900][size=4]**Eclipse**[/color][/size]](http://www.eclipse.org/)


[[color=#bd5900][size=4]**Emacs**[/color][/size]](http://www.gnu.org/software/emacs/)


[[color=#bd5900][size=4]**Geany**[/color][/size]](http://geany.uvena.de/)


[[color=#bd5900][size=4]**KDevelop**[/color][/size]](http://kdevelop.org)


[[color=#bd5900][size=4]**Netbeans**[/color][/size]](http://www.netbeans.org/)


[[color=#bd5900][size=4]**Vim**[/color][/size]](http://www.vim.org/)


[[color=#bd5900][size=4]**Python 2.5**[/color][/size]](http://www.python.org/)[/INDENT]






[color=#808080][size=5]**Sound/Video Editors and Disc Burning Utilities**[/color][/size]



[INDENT][[color=#bd5900][size=4]**Audacity**[/color][/size]](http://audacity.sourceforge.net/)


[[color=#bd5900][size=4]**Avidemux**[/color][/size]](http://fixounet.free.fr/avidemux/)


[[color=#bd5900][size=4]**DeVeDe**[/color][/size]](http://www.rastersoft.com/programas/devede.html)


[[color=#bd5900][size=4]**GnomeBaker**[/color][/size]](http://sourceforge.net/projects/gnomebaker/)


[[color=#bd5900][size=4]**K3B**[/color][/size]](http://k3b.plainblack.com/)


[[color=#bd5900][size=4]**Kino**[/color][/size]](http://www.kinodv.org/)


[[color=#bd5900][size=4]**LiVES**[/color][/size]](http://lives.sourceforge.net/)


[[color=#bd5900][size=4]**Vive**[/color][/size]](http://vive.sourceforge.net/)[/INDENT]






[color=#808080][size=5]**Web Browsers**[/color][/size]



[INDENT][[color=#bd5900][size=4]**Epiphany**[/color][/size]](http://www.gnome.org/projects/epiphany/)


[[color=#bd5900][size=4]**Firefox**[/color][/size]](http://www.mozilla.com/en-US/firefox/)


[[color=#bd5900][size=4]**Konqueror**[/color][/size]](http://www.konqueror.org/)[/INDENT]






[color=#808080][size=5]**Other Programs**[/color][/size]



[INDENT][[color=#bd5900][size=4]**AllTray**[/color][/size]](http://alltray.sourceforge.net/)


[[color=#bd5900][size=4]**GNASH**[/color][/size]](http://www.gnashdev.org/)


[[color=#bd5900][size=4]**Gparted**[/color][/size]](http://gparted.sourceforge.net/)


[[color=#bd5900][size=4]**Nouveau**[/color][/size]](http://nouveau.freedesktop.org/wiki/)


[[color=#bd5900][size=4]**Qalculate**[/color][/size]](http://qalculate.sourceforge.net/)


[[color=#bd5900][size=4]**Tomboy Notes**[/color][/size]](http://www.gnome.org/projects/tomboy/)


[[color=#bd5900][size=4]**WINE**[/color][/size]](http://www.winehq.org/)[/INDENT]






[color=#cbc8a9][b]I made this list because I realized how long it took, for me, to discover even a small portion of these apps when I first started using Linux. Hopefully someone new to Linux or looking for programs they have never used finds this helpful.

The "Installation" part of this list is currently incomplete. All of the application names lead to its project site.  Posting how to install one of these programs, another program you think should be on this list, a revision I should make to the organization of the list, or notifying me of any mistake/broken link on the list would help me a lot. I will be constantly updating this. Enjoy![/b][/color]

---

### Post by corney91 on 2007-08-26
I think [gmusicbrowser (http://squentin.free.fr/gmusicbrowser/gmusicbrowser.html)]("http://squentin.free.fr/gmusicbrowser/gmusicbrowser.html") should be added to the list.

---

### Post by smartboyathome on 2007-08-26
K3B isn't a video editor, it is a disc burner. Also, I think audacious and Kolourpaint need to be added. Scribus isn't a very good replacement to InDesign (because it 1 cannot open an InDesign document and 2 cannot import very much).

Edit: oops! I missed you including audacious.

---

### Post by Dark Star on 2007-08-26
Awesome work bro :) People try adding things instead of accusing him :p Awesome again .. Keep it up :) I'll add soon :D

---

### Post by smartboyathome on 2007-08-26
Zim Desktop Wiki needs to be added. :D

---

### Post by TheWiseNoob on 2007-08-26
-Added Songbird
-Added Zim Desktop Wiki
-Added Kolourpaint
-Added gmusicbrowser
-Group "Sound and Video Editors" changed to "Sound/Video Editors and Disc Burning Utilities"
-Added Audacious
-Updated XMMS to XMMS2

---

### Post by TheWiseNoob on 2007-08-26
Sorry for double post.

[COLOR=#383838] -Added Neverball, Scorched3D, and Stepmania to "Games and Emulators"
-Group "Linux Games" changed to "Games and Emulators"
-Added Alien Arena 2007 Installation Guide
-Added Emerald Installation Guide
-Added Avant Window Navigator Installation Guide
-Added Screenlets Installation Guide[/COLOR]

---

### Post by Lord Illidan on 2007-08-26
I like the list.

Will you add Programming IDEs/Editors.

Eclipse,Kdevelop,Geany,Anjuta could all be added to that list.

Also, personally this would be better in a webpage or a wiki with each app having a link to an installation howto, as the way it's going it seems that it's getting pretty large, but nice effort.

---

### Post by Fbot1 on 2007-08-26
Much better:
KDE:
[HTML]
BitTorrent Clients
    Azureus
    Qbittorrent

EyeCandy
    Avant Window Navigator(AWN)
    Emerald
    Compiz Fusion

File Browser/Search

Games and Emulators
    Battle for Wesnoth
    Nexuiz
    Tremulous

Graphics
    Blender
    Inkscape
    Krita

Office
    OpenOffice.org
    Scribus

Text editors
   Xemacs
   Microemacs
   Vim

Other Programming tools
    CMake
    GNU Debugger
    GCC
    Netwide Assembler

Music and Video
    Amarok
    Mplayer
    MythTV

FTP Programs
    FileZilla
    gFTP

Chat
    Kopete
    Mumble
    Pidgin

Sound/Video Editors and Disc Burning Utilities
    Audacity
    K3B

Web Browsers
    Firefox
    Konqueror
    Opera

Other Programs
    GNASH
    Scilab
[/HTML]

Gnome:
[HTML]
BitTorrent Clients
    Azureus
    Deluge

EyeCandy
    Avant Window Navigator(AWN)
    Emerald
    Compiz Fusion

File Browser/Search
    Beagle

Games and Emulators
    Battle for Wesnoth
    Nexuiz
    Tremulous

Graphics
    Blender
    The GIMP
    Inkscape

Office
    Abiword
    Gnumeric Spreadsheet
    OpenOffice.org
    Scribus

Text editors
   Xemacs
   Microemacs
   Vim

Other Programming tools
    CMake
    GNU Debugger
    GCC
    Netwide Assembler

Music and Video
    Mplayer
    MythTV

FTP Programs
    FileZilla
    gFTP

Chat
    Mumble
    Pidgin

Sound/Video Editors and Disc Burning Utilities
    Audacity

Web Browsers
    Firefox
    Opera

Other Programs
    GNASH
    Scilab
[/HTML]

Terminal:
[HTML]
BitTorrent Clients
    rTorrent
File Browser/Search


Games and Emulators
    Nethack

Office
    

Text editors
   Xemacs
   Microemacs
   Vim

Other Programming tools
    CMake
    GNU Debugger
    GCC
    Netwide Assembler

Music 

FTP Programs
    

Chat
    

Sound/Video Editors and Disc Burning Utilities
    

Web Browsers
  
    Links2

Other Programs
       ZSH
[/HTML]

---

### Post by smartboyathome on 2007-08-26
Mind if I compile this in Zim? I may distribute it sometime, or may just use it for reference :D

EDIT: Vim... ick, talk about an editor that shouldn't exist anymore.

---

### Post by Fbot1 on 2007-08-26
> **smartboyathome said:**
> Mind if I compile this in Zim? I may distribute it sometime, or may just use it for reference :D

EDIT: Vim... ick, talk about an editor that shouldn't exist anymore.

Too be honest I don't like it either. :)

---

### Post by PartisanEntity on 2007-08-26
I like how you offer the installation instructions, it would be great for new members, perhaps we can combine the valuable info from [this thread]("http://ubuntuforums.org/showthread.php?t=382137") with the idea of this thread and end up with one mega thread that is nicely organised, easy to follow and offers installation instructions.

edit: [another thread]("http://ubuntuforums.org/showthread.php?t=533529") with 'cool' applications.

---

### Post by TheWiseNoob on 2007-08-26
> **smartboyathome said:**
> Mind if I compile this in Zim? I may distribute it sometime, or may just use it for reference :D

EDIT: Vim... ick, talk about an editor that shouldn't exist anymore.

Yeah, it's alright with me. 

Thanks for posting suggestions. I added a "Programming IDEs" Group and added the apps suggested and moved Python 2.5 to the group.

*EDIT* Added Netbeans too

---

### Post by Fbot1 on 2007-08-26
> **TheWiseNoob said:**
> Yeah, it's alright with me. 

Thanks for posting suggestions. I added a "Programming IDEs" Group and added the apps suggested and moved Python 2.5 to the group.

*EDIT* Added Netbeans too

I think you should trim the list.

---

### Post by TheWiseNoob on 2007-08-26
> **Fbot1 said:**
> I think you should trim the list.

I plan on getting 100 apps and then not adding anymore. I will just need help updating links and such.

---

### Post by Dual Cortex on 2007-08-26
You're missing a GREAT IDE: Code::Blocks

[www.codeblocks.org](www.codeblocks.org)

To use, browse their nightly builds and install one of their pre-compiled packages.

---

### Post by Ciego on 2007-08-26
Thanks for the great list.  

You need to add a 
```

sudo apt-get upgrade 
```

before step #4 of the compiz fusion instructions though.

---

### Post by kahrn on 2007-08-26
This list could really do with being put on the ubuntu wiki (or a private wiki) so people can update and contribute easier. :)

---

### Post by Henaro on 2007-08-26
You should add rtorrent and irssi.

---

### Post by kahrytan on 2007-08-26
Remove NVU. It's not updated anymore.  Amaya is a better choice. The application is jointly developed by W3C and the WAM project at INRIA.

---

### Post by Spr0k3t on 2007-08-26
One that should be added to go along with NVU is Aptana.  It uses the Eclipse IDE front end and is an html editor.  Very slick...

[http://www.aptana.com/](http://www.aptana.com/)

---

### Post by izanbardprince on 2007-08-26
You forgot Sauerbraten!

---

### Post by EvanCarroll on 2007-08-26
Where is Open Arena? (the most popular free FPS that I know about)

---

### Post by TheWiseNoob on 2007-08-26
Updated. Getting close to 100. Just a few more apps.

Can someone please suggest a wiki I can put this on?

---

### Post by Rupertronco on 2007-08-26
Affinity search definitely belongs on this list.

---

### Post by Spr0k3t on 2007-08-26
> **TheWiseNoob said:**
> Can someone please suggest a wiki I can put this on?

Why not drop it on the wiki.ubuntu.com temporarily until you can find a wiki you want to use?

---

### Post by ErikTheRed on 2007-08-26
Warsow should be added under games

---

### Post by EXCiD3 on 2007-08-26
All i have to say is <3.... You rule guys! I'm gonna start checkin out this stuff. Granted i have heard of much of this, just havent decided to try some out yet...Thanks!

---

### Post by happysmileman on 2007-08-26
Just me or is this a bit biased towards GNOME apps?

---

### Post by Fbot1 on 2007-08-26
> **happysmileman said:**
> Just me or is this a bit biased towards GNOME apps?

I guess he/she could make more then one list.

---

### Post by smartboyathome on 2007-08-26
Add some virtualization software. VirtualBox, QEMU, and VMWare Server and the big three. Also, for web browsers, there is Opera, and (if you don't mind adding another piece from the mozilla family) seamonkey. For "other", there is gtk-recordmydesktop (it records a video of your desktop), and WICD, a network manager for Ubuntu. Also, I like the idea of adding a KDE and a GTK (and a other if necessary) list.

EDIT: When I am done with the Zim wiki section, where should I post it?

---

### Post by thisllub on 2007-08-26
Ardour and Rosegarden are the most powerful music recording / editing programs.

---

### Post by Fbot1 on 2007-08-26
> **smartboyathome said:**
> Also, I like the idea of adding a KDE and a GTK (and another if necessary) list.


Small X apps and terminal apps are the only other lists I can think of but I'd imagine that most people don't really cares.

---

### Post by happysmileman on 2007-08-26
What about having on the one page (if it's on a wiki or something) the list (maybe more than 100) with subsections for KDE/GNOME.

Or What about a list showing ONE program for each purpose (one bittorrent client, one IDE etc.) for each DE (so there'd be a GNOME bittorrent client, a KDE one, one for either, and a terminal one).
the program would be voted for out of a list of the best ones we can think of.

Though this is probably going to have to be a completely seperate list

---

### Post by smartboyathome on 2007-08-26
I am going to work on getting the origional list done in Zim before I even think about a GTK and a Qt list. Will post when I am done.

---

### Post by Fbot1 on 2007-08-26
> **happysmileman said:**
> Or What about a list showing ONE program for each purpose

As long as you don't get too strict with it that sounds fine to me.

---

### Post by Ciego on 2007-08-26
I made a mistake in my earlier suggestion .... it should be 

```
sudo apt-get update
```

before step #4 for the compiz-fusion

---

### Post by Fbot1 on 2007-08-26
I'm too damn impatient, just use this for now:
[http://en.wikipedia.org/wiki/User:Fbot1/List_of_the_Best_Open-Source_Apps](http://en.wikipedia.org/wiki/User:Fbot1/List_of_the_Best_Open-Source_Apps)

---

### Post by happysmileman on 2007-08-26
> **Fbot1 said:**
> I'm too damn impatient, just use this for now:
[http://en.wikipedia.org/wiki/User:Fbot1/List_of_the_Best_Open-Source_Apps](http://en.wikipedia.org/wiki/User:Fbot1/List_of_the_Best_Open-Source_Apps)

Oh sorry, didn't realise that was one of your user-pages, shouldn't have done that, though I didn't remove anything so should be easy to fix

---

### Post by Fbot1 on 2007-08-26
> **happysmileman said:**
> Oh sorry, didn't realise that was one of your user-pages, shouldn't have done that, though I didn't remove anything so should be easy to fix

Done what?

---

### Post by happysmileman on 2007-08-26
> **Fbot1 said:**
> Done what?

Added in the bullets, ie made an unordered list out of them

---

### Post by Fbot1 on 2007-08-26
> **happysmileman said:**
> Added in the bullets, ie made an unordered list out of them

I think it's better that way.

---

### Post by happysmileman on 2007-08-26
Ah ok never mind then

---

### Post by wersdaluv on 2007-08-27
Wow. I have always been in the Community Cafe, but only digg informed me about the existence of this thread.

Okay. By the way. I think that BasKet NotePads should be on the list. It is my most favorite app.

---

### Post by Dark Star on 2007-08-27
--------------------------------------------------------------------------
 **Software Name:** avast! Linux Home Edition
 **Distro**:Any Distros
 **Purpose:** Provide Ultimate security at free of cost.
 **Extra Info:**Very easy to use and its free of cost and provide goo security
 **Download:** [Click Here]("http://www.avast.com/eng/download-avast-for-linux-edition.html")
 **Registration:-** [Click Here]("http://www.avast.com/eng/home-registration.php")
--------------------------------------------------------------------------
 
--------------------------------------------------------------------------
 **Software Name**:MPlayer
 **Distro**:Any Distross
 **Purpose**:Video player for just any audio and video format. Have gui written in gtk which you may run by gmplayer.
 **Extra Info**:can play any format.
 **Site:-**[Entering MPlayer homepage]("http://www.mplayerhq.hu/")
--------------------------------------------------------------------------
 
 
--------------------------------------------------------------------------
 **Software Name:**unrar
 **Distro**:Any Distross
 **Purpose**:The unRAR utility is a freeware program distributed with source code and developed for extracting, testing and viewing the contents of archives created with the RAR archiver.
 **Extra Info:**Can zip unzip files.
 **Download:** [ Click Here]("http://www.linuxsoft.cz/en/redirect.php?id_download=9811")
-----------------------------------------------------------
 
--------------------------------------------------------------------------
 **Software Name**: OpenOffice
 **Distro**:Any Distross
 **Purpose**: OpenOffice.org is both an Open Source product and a project. The product is a multi-platform office productivity suite. It includes the key desktop applications, such as a word processor, spreadsheet, presentation manager, and drawing program, with a user interface and feature set similar to other office suites’. Sophisticated and flexible, OpenOffice.org also works transparently with a variety of file formats, including those of Microsoft Office.
 **Home Page**:[OpenOffice.org: Home]("http://www.openoffice.org/")
--------------------------------------------------------------------------
 
--------------------------------------------------------------------------
 **Software Name**:GCC
 **Distro**:ANy Distross
 **Purpose**:GCC is the GNU Compiler Collection, which currently contains front ends for C, C++, Objective-C, Fortran, Java, and Ada, as well as libraries for these languages (libstdc++, libgcj,...).
 **Extra Info:**Altenate ofGCC, Borland C++, Visual C++, ...
 **Home Page:** [GCC, the GNU Compiler Collection - GNU Project - Free Software Foundation (FSF)]("http://gcc.gnu.org/")
 **Down Load:-** [Click Here ]("http://www.linuxsoft.cz/en/redirect.php?id_download=10128")
--------------------------------------------------------------------------

--------------------------------------------------------------------------
 **Software Name:**Wolfenstein: Enemy Territory
 **Distro:** Any Distross
 **Purpose:** Gaming 
 **Extra Info:** An FPS game specially created for Linux User. This game is meant to be played online with full throttle.
 **Home Page:** [Click Here]("http://games.activision.com/games/wolfenstein/")
--------------------------------------------------------------------------
 
--------------------------------------------------------------------------
 **Software Name:** Racer
 **Distro:** Any Distross
 **Purpose**:Gaming
 **Extra Info:**Racer is a free cross-platform car simulation project (for non-commercial use), using professional car physics papers to achieve a realistic feeling. Cars, tracks and such can be created relatively easy (compared to other, more closed, driving simulations). The 3D and other file formats are, or should be, documented. Editors and support programs are also available to get a very customizable and expandable simulator. OpenGL is used for rendering.
 **Home Page: **[Click Here]("http://www.racer.nl/")
 **Download: **[Click Here]("http://www.linuxsoft.cz/en/redirect.php?id_download=22758")
--------------------------------------------------------------------------
 
--------------------------------------------------------------------------
 **Software Name**: GNOME Commander
 **Distro: **Any DIstross
[b][Extra Info:/B]GNOME Commander is a fast and powerful graphical file manager for the Gnome desktop environment, it has a "two-pane" interface in the tradition of Norton and Midnight Commander.
 **Home Page:** [Click Here]("http://www.nongnu.org/gcmd/")
 **Download: **[Click Here]("http://www.linuxsoft.cz/en/redirect.php?id_download=23630")
--------------------------------------------------------------------------

--------------------------------------------------------------------------
 **Software Name:**Typing Trainer
 **[B]Distro:**[/B]Any Distross
 **Purpose**:To increase typing speed
 **Extra Info**:Typing Trainer is designed for exercising typing speed and typing accuracy, by providing an environment to type in a copy of an original text within a specific time period. It also has the ability to store the results of such an exercise for exam purposes.
 **Home Page**: [Click Here]("http://typingtrainer.sourceforge.net/") 
 **Dowloads**: [Click Here]("http://www.linuxsoft.cz/en/redirect.php?id_download=10383")
--------------------------------------------------------------------------
--------------------------------------------------------------------------
 **Software Name:** Bluetooth remote-control
 **Distro:**Any Distross
 **Extra Info:** Bluetooth remote-control makes it possible to use your Bluetooth-capable cell phone as a mouse in X, which is useful for remote controling your computer.
 **Download:** [Click Here]("http://www.linuxsoft.cz/en/redirect.php?id_download=32201")
 **Home Page**: [Click Here]("http://folk.ntnu.no/havardhu/")
--------------------------------------------------------------------------
 
--------------------------------------------------------------------------
 **Software Name**:FireFox
 **Distro**:Any Distross
 **Purpose:**Web Browsing
 **Extra Info**:Mozilla FireFox empowers you to accomplish your online activities faster, more safely and efficiently than any other browser, period. Built with Tab browsing, popup blocking and a number of other seamless innovations, Mozilla FireFox stands out ahead.
 **Download:**[ Click Here]("http://www.linuxsoft.cz/en/redirect.php?id_download=5644")
 **Home Page:** [Click Here]("http://www.mozilla.org/products/firefox/")
--------------------------------------------------------------------------
 
 
--------------------------------------------------------------------------
 **Software Name** Opera
 **Distro:**Any Distross
 **Purpose**:Web Browsing
 **Extra Info**:Goals: cross-platform (thanks to QT library), very ergonomic (greatly customizable GUI), high speed (higher than IE), tabbed-browsing, built-in e-mail client, pop-up killer,...
Very useful is session saver: At start Opera can restore it's state before last end. Everything in 4MB!
 
 **Displaying: **Obviously CSS styles and JavaScript (Java is optional). Version 7.x displays pages excellent. By my web-designer experience: what displays good in Opera will also be good in Mozilla and IE.
 **Home Page:** [Opera web browser: Homepage]("http://www.opera.com/")
--------------------------------------------------------------------------

--------------------------------------------------------------------------
 **Software Name:** CPUtemp
 **Distro:** Any distrss
Purpose:To measure the temperature of CPU
 **Extra Info: **CPUtemp is a Gnome applet that displays the current CPU temperature in the tray. It is written in Perl using Perl-Gtk2 bindings. It uses the syskernel interface to read temperature sensor data.
 **Home Page:** [http://cputemp.sourceforge.net/](http://cputemp.sourceforge.net/)
--------------------------------------------------------------------------
--------------------------------------------------------------------------
 **Software Name:** KHealthCare
 **Distro:** Any Distross
 **Purpose: **Hardware Monitoring 
 **Extra Info:** KHealthCare is a hardware monitoring program, running under Linux / KDE.
 **Home Page: **[http://homepages.fh-giessen.de/%...care/main.html]("http://homepages.fh-giessen.de/%7Ehg7229/khealthcare/main.html")
--------------------------------------------------------------------------
 
--------------------------------------------------------------------------
 **Software Name:**Ghost for Linux
 **Distro:**Any distross
 **Purpose:** Backup and Partition Manager
 **Extra Info:** Ghost for Linux is a hard disk and partition imaging and cloning tool similar to Norton Ghost(c). The created images are optionally compressed and transferred to an FTP server. The included kernel supports almost every common network interface, ATA and serial-ATA drives. The extended kernel on CD supports SCSI and several 1000 MBit network cards. It comes as 2 boot/root disks or a bootable CD image with an ncurses GUI.
 **Home Page:** [Confixx Professional]("http://g4l.networks-ltd.de/")
--------------------------------------------------------------------------
 
--------------------------------------------------------------------------
 **Software Name:** Everest QDictionary
 **Distro:** Any Distross
 **Purpose:** To Search word meaning easily.
 **Extra Info:** It includes 35 dictionaries with almost 3.000.000 records. Everest Dictionary is the greatest of the free dictionaries available to the public. Covers all main european languages
The possibility to search words in many dictionaries. It is possible to search words across many dictionaries. It monitors the clipboard; in any program, a simple copy of the word to the clipboard using "Copy" command will have as effect the automatic search of the word in the dictionary.
 **Home Page:** [Free Soft - Freeware applications]("http://www.free-soft.ro/")
--------------------------------------------------------------------------
--------------------------------------------------------------------------
 **Software Name:** XNVIEW
 **Distro: **Any Distros
 **Purpose:** Image Editing/Viewing
 **Extra Info:** XnView is image viewer and editor. It can import 400 from different grafical formats and it can export to 50 formats. Basic operations with images (resize, change of color depth, filters..) Conversions of pictures can be also made in console (usefull for shell scripts).
 **Home Page:** [Free graphic and photo viewer - XnView - GRAPHIC VIEWER]("http://www.xnview.com/")
--------------------------------------------------------------------------
--------------------------------------------------------------------------
 **Software Name:** Corel PHOTO-PAINT
 **Distro:** ANy Distross
 **Purpose: **Image editing 
 **Extra Info:** Corel Photo-Paint is the well known image creation and photo editing application.
 
While many may prefer GIMP for quick and dirty image editing, Corel Photo-Paint may become the new favorite for batch processing of images and complex graphical effects.
 **Home Page:** [Corel Corporation - Home of CorelDRAW, WordPerfect, Paint Shop Pro, Photo Album and Painter]("http://www.corel.com/")
--------------------------------------------------------------------------
 
--------------------------------------------------------------------------
 **Software Name**: Moonlight 3D Atelier
 **Distro:** Any distross
 **Purpose:**3d Animation
 **Extra Info**:Moonlight 3D is a free and open source, cross platform, 3D software package. Moonlight 3D supports such feature as: 3D modelling, 3D animation, NURBS based modelling, Bezier curve based modelling, texture mapping, GStreamer integration, Ray-tracing, Radiosity, and more.
 **Home PAge**: [http://www.moonlight3d.com/](http://www.moonlight3d.com/)
--------------------------------------------------------------------------
--------------------------------------------------------------------------
 **Software Name**:GIMP
 **Distro**:Any Distross
 **Purpose:** Image Editing
 **Extra Info: **GIMP is an acronym for GNU Image Manipulation Program. It is a freely distributed piece of software suitable for such tasks as photo retouching, image composition and image authoring.
 **Home Page**: [GIMP - The GNU Image Manipulation Program]("http://www.gimp.org/")
--------------------------------------------------------------------------

--------------------------------------------------------------------------
**Software Name** Openquicktime
**Distro:**Any Distross
**Purpose**:Media Player 
**Extra Info:**OpenQuicktime aims to be a portable library for handling Apples QuickTime popular media files on Unix-like environments. It is aim is to provide encoding, authoring and editing support as well as video playback.
**Home Page:** [OpenQuicktime - a new Quicktime Library]("http://www.openquicktime.org/")
--------------------------------------------------------------------------

--------------------------------------------------------------------------
**Software Name:**XviD
**Distro:**Any Distros
**Purpose**:Media Player for XVID files
**Extra Info**:XviD is a high-quality ISO MPEG-4 compliant video codec.
**Home Page:**[Xvid.org: Home of the Xvid Codec]("http://www.xvid.org/")
--------------------------------------------------------------------------

--------------------------------------------------------------------------
**Software Name:** SIM (Simple Instant Messenger)
**Distro:** Any Distross
**Purpose: **Online Chat
**Extra Info**: An instant messagner used for online chatting...
**Home Page:** [Please wait...]("http://sim-icq.sourceforge.net/")
--------------------------------------------------------------------------

--------------------------------------------------------------------------
[B]Software Name: Netscape 7.2
Distro: Any Distros
Purpose: Web Browsing
Extra Info:[/B]In addition to high-speed browsing and instant-messaging capabilities, Netscape features one-click searching from the address bar; Quick Launch, which reduces the browser start-up time; Click-to-Search, which allows users to select a word within a Web page and search; improved instant messaging, including support for buddy icons, file transfers, and buddy alerts; and tabbed browsing, which allows users to view multiple Web pages in a single browser window. Netscape 7.2 offers improved pop-up blocking and enhanced security. New features include extended address-bar searching, enhanced tabbed browsing, improved downloading, and new printing options.
**Home Page:**[Home Page » Netscape.com]("http://home.netscape.com/")
--------------------------------------------------------------------------

--------------------------------------------------------------------------
**Software Name**:aMSN
**Distro:** Any Distros
**Purpose:** Online Chatting
**Extra Info:** A MSN Messenger clone for Linux.
**Home Page;** [Alvaro's Messenger]("http://amsn.sourceforge.net/")
--------------------------------------------------------------------------

--------------------------------------------------------------------------
**Software Name: **Salamander
**Distro:** Any Distros
**Purpose:** Web Browsing
**Extra Info: **Salamander is a web browser for Linux (and possibly Unix) written in C,that uses the Gnome2/GTK2 libraries.It also uses the Mozilla engine Gecko for compatibilty issues with the internet standards.
**Home Page:**
--------------------------------------------------------------------------

--------------------------------------------------------------------------
**Software Name:** libdvdcss
**Distro:** ANy Distros
**Purpose:** DVD Player
**Extra Info:** libdvdread provides a simple foundation for reading DVD video disks. It provides the functionality that is required to access many DVDs. It parses IFO files, reads NAV-blocks, and performs CSS authentication and descrambling.
**Home Page:** [VideoLAN developers - libdvdcss]("http://developers.videolan.org/libdvdcss/index.html")
--------------------------------------------------------------------------

--------------------------------------------------------------------------
**Software Name:**Gaim
**Distro:** Any distros mainly comes pre-installed
**Purpose:**Instant Messaging 
**Extra Info: **Gaim is a multi-protocol instant messaging client for Linux, BSD, MacOS X, and Windows. It is compatible with AIM (Oscar and TOC protocols), ICQ, MSN Messenger, Yahoo, IRC, Jabber, Gadu-Gadu, and Zephyr networks. Gaim users can log in to multiple accounts on multiple IM networks simultaneously. This means that you can be chatting with friends on AOL Instant Messenger, talking to a friend on Yahoo Messenger, and sitting in an IRC channel all at the same time.
Home Page: [News - Pidgin]("http://gaim.sourceforge.net/")
--------------------------------------------------------------------------

--------------------------------------------------------------------------
Software Name: Yahoo! Messenger for Unix
Distro: Unix.
Purpose: Instant Messaging 
Extra Info: Yahoo! Messenger for Unix.
Home Page: [Unix Version - Yahoo! Messenger]("http://messenger.yahoo.com/messenger/download/unix.html")
--------------------------------------------------------------------------

--------------------------------------------------------------------------
Software Name: linphone
**Distro::** Any Distross
**Purpose::** PC to PC call
**Extra Info:** Linphone allows you to make two-party phone calls using an IP network. Easy to use, it has a gnome graphical interface. As it uses a very minimal implementation of the Session Initiation Protocol (SIP) in order to establish the call, it MAY work with other sip-phones. RTP is used to transport voice over IP.
**Home Page:**[Bienvenue - Linphone, an open-source sip video-phone for linux and windows]("http://www.linphone.org/")
--------------------------------------------------------------------------

--------------------------------------------------------------------------
**Software Name:**Kmess
**Distro: **KDE Distross
**Purpose: **Instant Messaging
**Extra Info:** MSN Messanger for KDE.
**Home Page:**[KMess, MSN Messenger for Linux - Home]("http://kmess.sourceforge.net/")
--------------------------------------------------------------------------

--------------------------------------------------------------------------
**Software Name:** libbeep
**Distro:** Any Linux Distros
**Purpose**: Music Player.
**Extra Info:** A way to get music from your PC beeper in any Linux program.
**Home Page: **[Index of /~raine/pub/software/beeper]("http://www.infa.abo.fi/%7Eraine/pub/software/beeper/")
--------------------------------------------------------------------------

--------------------------------------------------------------------------
**Software Name:**Gzilla
**Distro:** Any Distros
**Purpose:** Web Browsing 
**Extra Info:** Gzilla is a Web browser written in the Gtk+ framework.
**Home Page: **[Gzilla]("http://www.levien.com/gzilla/")
--------------------------------------------------------------------------


Will be updating more .. So enjoy Linux and say good bye to Windows..
[B]
Always remember: The PC say Install Windows or better so every time 1 must install linux as Linux is better than Windows :lolflag: [/B] 

[B]Note: If a software is posted 2 or more times plz tell/inform so that I may correct it. Some would have been added already so plz do not mind :guitar:

Regards
[/B]

---

### Post by TheWiseNoob on 2007-08-27
I'll be updating the list again soon and posting a thread with a link to a wiki. Keeps suggesting programs.

---

### Post by wersdaluv on 2007-08-27
The great file managers, Dolphin and PCManFM, should be here too.

---

### Post by Dark Star on 2007-08-27
> **wersdaluv said:**
> The great file managers, Dolphin and PCManFM, should be here too.
2nd that I love Pac man FM awesome :D

---

### Post by sacherjj on 2007-08-27
I love Scribes.  It is a text editor with highlighting and suggestions, great for writing code.  It is in the process of getting added to the repositories, but a .deb package is available from getdeb.

---

### Post by Iarwain ben-adar on 2007-08-27
Bookmarked ^^

Thx for the list


Iarwain

---

### Post by Foxmike on 2007-08-27
What about Digikam (awsome photo manager), and k9copy (great counterpart of DVDShrink)?

---

### Post by porkrind on 2007-08-27
You can find a doc on HowtoForge here: [http://www.howtoforge.com/hyperic_hq_on_ubuntu704](http://www.howtoforge.com/hyperic_hq_on_ubuntu704)

This list seems mostly focused on desktop apps. Thought it might be nice to throw a bone to sysadmins, too :@)

-John Mark

---

### Post by awakatanka on 2007-08-27
Digikam [http://www.digikam.org/](http://www.digikam.org/)
Super karamba 
Googledesktop search [http://desktop.google.com/linux/](http://desktop.google.com/linux/)
Wengophone [http://www.openwengo.org/](http://www.openwengo.org/)
Krita [http://www.koffice.org/krita/](http://www.koffice.org/krita/)

Need to be in, but thats my opninion, think some are beter then what is already in.

---

### Post by fenderocker on 2007-08-29
I think that VLC should be higher up on the list than it is  now... Not having to download codecs is really helpful.

Great list!

---

### Post by RAV TUX on 2007-08-29
KSudoku
SolarWolf

---

### Post by ThinkBuntu on 2007-08-29
SPE - Stan's Python Editor

---

### Post by therrmann on 2007-08-30
Xfig is an absolute necessity for my work.  I'm a college physics teacher, and I must have by now over a thousand .eps files (as well as .png, etc) made with xfig.   If you use LaTeX, it's necessary to have an easy-to-use and rock-solid app for making figures.

---

### Post by urukrama on 2007-08-30
If you want a terrific file manager, go for krusader. There is no better graphical dual pane file manager for Linux.

---

### Post by jkozura on 2007-08-30
Webmin.
I have been using Webmin on practically every Linux system I use since I found it in an old version of Caldera back in 2000 after seeing something written about it in a Novell magazine.

---

### Post by Anzan on 2007-09-01
Thanks. I found Amaya through this list and it looks very promising.

---

### Post by rabid9797 on 2007-09-01
forgot opera

---

### Post by RomeReactor on 2007-09-01
I second [Mplayer]("http://www.mplayerhq.hu/design7/news.html"); Dark Star already suggested it. As for installing Alien Arena through Synaptic, I don't know of any repository that carries it. To install it, you either download it from their site or download the .deb files on [GetDeb]("http://www.getdeb.net/app.php?name=Alien+Arena+2007").

And for people still suggesting Opera--as good as it is, it's [proprietary]("http://www.opera.com/support/new2opera/buy/license/index.dml"), not open source.

---

### Post by sda5150 on 2007-09-02
I think for audio apps, the following needs to be added:

Ardour
LMMS

:guitar:

---

### Post by Sam Lars on 2007-09-03
[Hugin]("http://en.wikipedia.org/wiki/Hugin_(software)") for making panoramas.
[Mousepad]("http://www.xfce.org/projects/mousepad/") is a much more lightweight text editor.  Even though it's for Xfce, it works great in Gnome.
[Swiftfox]("http://www.getswiftfox.com/") is just optimized Firefox, if you feel that it would fit in the list.
[SoundConverter]("http://soundconverter.berlios.de/") for converting audio files.
[Gtick]("http://www.antcom.de/gtick/") is a good metronome.
[EasyTAG]("http://easytag.sourceforge.net/") is a great audio file tagging application.
[Gtk-Gnutella]("http://gtk-gnutella.sourceforge.net/en/?page=news") for file sharing.
[Firestarter]("http://www.fs-security.com/") for managing the firewall.

If any of these have already been mentioned/rejected, apologies.

---

### Post by Slychilde on 2007-09-05
Opera is closed-source or I would agree with you.  Epiphany is quick, although I wouldn't use it as a sole webrowser.

+1 for Qalculate and Agave and Mirage.

---

### Post by Bothered on 2007-09-17
OpenSSH (server) - Secure command line remote access
FreeNX - Secure desktop remote access
htop - top with added functionality
qemu - Virtualisation software
GHex - Binary file editor
GRAMPS - Geoeology database program (family tree generator)

Sorry if these have been listed already :-)

---

### Post by ineedaname on 2007-09-18
I believe one of the repositories listed for avant-window-navigator was changed today, and no longer has its checksum:

```

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

http://download.tuxfamily.org/syzygy42/dists/feisty/Release: No MD5Sum entry in Release file /var/lib/apt/lists/download.tuxfamily.org_syzygy42_dists_feisty_Release

```

---

### Post by soxs on 2008-01-02
Swiftweasl should be added, it's a opensource full gpl, architecture optimized firefox and does not include any compiled in proprietary code as Firefox does.

---

### Post by M$LOL on 2008-01-02
[Emesene]("http://emesene.org") should be added imo.

---

### Post by Tom Mann on 2008-01-02
Ardour and LMMS please! (via Ubuntustudio)

---

### Post by molom on 2008-01-15
Kompozer (Web authorer), Spicebird and freemind (Brainstorming app) are good open source apps.

---

### Post by soxs on 2008-01-16
2 math programs for plotting, solving equations:
qtiplot [http://soft.proindependent.com/qtiplot.html](http://soft.proindependent.com/qtiplot.html)
qualculate
3D Moddeling Misfit Model 3D [http://www.misfitcode.com/](http://www.misfitcode.com/)
Game: WorldOfPadman [http://worldofpadman.com/](http://worldofpadman.com/)

---

### Post by riger99 on 2008-03-12
There's a pretty cool new list here: [http://ubuntulinuxhelp.com/top-100-of-the-best-useful-opensource-applications/]("http://ubuntulinuxhelp.com/top-100-of-the-best-useful-opensource-applications/")
:)

---

### Post by isaiddurazoo on 2008-06-13
HEY IM TRYING TO START A UBUNTU YOUTUBE COMMUNITY MY CHANNEL IS [http://www.youtube.com/user/sold13r45](http://www.youtube.com/user/sold13r45) CHECK IT OUT IF YOU WANT

---

### Post by bgs100 on 2008-11-28
Atanks

---

### Post by -grubby on 2008-11-28
Awesome list, but you should fix those yellow fonts. Thanks :D

---

### Post by CJ Master on 2008-11-28
Good list, but I can't belive Teeworlds isn't on there >.>

---

### Post by wfp on 2008-12-08
Thank you for putting the time and effort to make this list for the community. Did not know about akregator, so i just installed it, and love the easy layout, and easy way to configure it. Thanks

---

### Post by halovivek on 2008-12-08
Thanks for posting i will try some.:lolflag:

---

### Post by tyk on 2009-01-29
In games, Foo-billiard is really cool. And scribus imports virtually anything, AFAIK.
tyk.

---

### Post by Neural oD on 2009-01-29
thanks - know most of them - quick browse - but looks like there are others i need to investigate

---

### Post by abhilashm86 on 2009-01-29
good list of apps,
htop- a terminal viewing and editing system progress
along with irssi needs to be added

---

### Post by NayC on 2009-05-12
Good work, for people reading the comments, Warsow should be in the games list!

---

### Post by munishvit on 2009-05-12
Great work...BUMP:P

---

### Post by nstorrs on 2009-05-12
I would like to toss Gnome-Do on top of the pile.  I can't seem to use my computer without it anymore.

---

### Post by .Maleficus. on 2009-05-12
abcde needs to be on there.  Simply the best audio ripper for Linux.  It rips to your specified format, searches CDDB for ID3 tags, is highly configurable and is lightweight.

---

### Post by chris4585 on 2009-05-12
Music and Video Players

add > Quodlibet

---

### Post by wcutrombonekid on 2009-06-08
does anyone know if there is any kind of music composition program around that is open source?  I'm very new to ubuntu, only had it on my computer now for a month or so and was wondering if there is anything that is comparative or at least similar to garage band or finale?  I've searched on here several times and searched tirelessly through the interwebs and have found nothing.  This would be a very usful thing to have since i am a musician.

---

### Post by Arathorn on 2009-06-09
Take a look at [this site](https://wiki.ubuntu.com/UbuntuStudio/PackageList). It's meant for Ubuntu spin-off Ubuntu Studio, but all those programs are available in standard Ubuntu as well. I'm don't know specificly what you're searching for, but I hope the description of the packages give enough information.

I'd like to add Warzone2100 to the list. It's a great 3D RTS that's still in heavy development.

---

### Post by xx58 on 2009-06-14
:rolleyes: Just Great. Very helpful.

---

### Post by Gatemaze on 2009-06-20
My two cents:

Unless you are running some very old version of ubuntu:

+Brasero replace Gnomebaker
+Transmission on torrent clients
+Opera should be more popular than Epiphany (and who uses konqueror as a webbrowser)
+Konqueror and Dolphin as file browsers maybe. Although you should maybe write in parentheses whether they are Gnome/KDE/XFCE. It's not really useful to have nautilus, dolphin and thunar all together.
+I can't even believe that mplayer is not on the list.
+Easytag for editing mp3 tags
+Checkgmail maybe
+Gnucash for keeping financial records
+Kparted instead of Gparted if you are a KDE user
+Gpaint instead of kolorpaint if you are a gnome user
+Grip for ripping cds to mp3s
+Sound Converter (there is also an equivalent for KDE) for converting different types of music files
+gtkpod for interaction with an ipod.
+Firestarter manager of firewall
+Abiword, Gnumeric can be summed up by the Gnome office. There is also a KDE office. Both are redundant since pretty much everyone uses OpenOffice nowadays.
+I don't think python 2.5 can be classified as an IDE.
+I think that the sound/video editors and disc burning utilities is quite poor...
+I think games should be left out... there can be quite a long list... Beyond the red line is another awesome game.

In general this is a good summary of useful programs... However, there should be some kind of distintion between the different desktop environments and they should count as one application since you will only need one. For example gnome users will use nautilus, kde users dolphin and xfce thunar... using nautilus in kde is just not efficient.

---

### Post by treesurf on 2009-06-20
> **nstorrs said:**
> I would like to toss Gnome-Do on top of the pile.  I can't seem to use my computer without it anymore.

+1.  Gnome-Do definitely belongs on the list.

---

### Post by rookcifer on 2009-06-20
> **happysmileman said:**
> Just me or is this a bit biased towards GNOME apps?

Yep.  The fact he/she put F-Spot on the list and forgot about the superior digiKam is proof.  And let's not forget about K9Copy.  Far better than any other DVD ripping tool.

---

### Post by k2t0f12d on 2009-06-30
[ushare]("http://ushare.geexbox.org/") is an easy to use multimedia server

---

### Post by conorsulli on 2009-08-08
1)
Google Chrome: available in an easy deb from google now, its still classed unstable but runs very well.

2)
Universal Applets: The new and improved Screenlet widgets.

3)
Google Gadgets: a sidebar & widgets, its available in qt and gtk.

Mplayer: handles pretty much any video file, with many frontends! such as gnome-mplayer,and my favorite "smplayer" etc... 
Shocked to be honest it aint on the list yet!! It definitely deserves a spot!

SMplayer : bringing mplayer with a qt frontend and theming ability!.

---

### Post by CJ Master on 2009-08-08
A bit of a warning, this topic was necromanced so the first post has some out-of-date installation instructions. Especially Compiz.

---

### Post by medya on 2009-10-31
among all the posts above, nobody mentined a Download Manager for linux, may be there is no good Dowload accelator .
pl
- D4x looks terreble and buggy and you can hardly finish a download using it .
- axel is wost application ever it was like designed 20 years ago . and noone works on it.
- Kget works fine (still no good compared to windows' Download Accelerator Plus (DAP))but it is for kde.
- Wget is stupid and buggy. and not as good as Kget.

---

### Post by soad6 on 2010-11-01
You should list DeVeDe for making movies, from AVI files.. it does an awesome job.

---

### Post by uRock on 2010-11-01
Thread closed.

---

