---
title: "Lxde on 13.10 has made things way better for me"
date: 2013-11-03
forum: Ubuntu, Linux and OS Chat
---

### Post by shantiq on 2013-11-03
changed my desktop after 4 years of struggling with Gnome and Unity to Lxde
a little while back since i discovered very late in the game that there were EASILY accessible alternatives
which are way lighter on a machine with specs which are not tremendous in 2013


[COLOR=#a52a2a]**Make ** sure you have to use your password to login so you can see the DE options when starting your session
**to do that from default Unity** enter login in search find user accounts and set to "off" then lock and reload[/COLOR]


[[IMG]http://img577.imageshack.us/img577/4980/6k4o.th.png[/IMG]]("http://img577.imageshack.us/img577/4980/6k4o.png")


All it takes was to open synaptic and install lxde or probably to run ```
sudo apt-get install lxde
```


then to click on ubuntu sign at login and pick lxde see photo
you can  also try xcfe4 and cinnamon and enlightenment and many others no doubt in same way [maybe one at a time not to clog up machine more]

Is is easy and does not mean you have to remove Unity or Gnome


[IMG]http://i.stack.imgur.com/Xm10N.png[/IMG]File Association


HERE ARE A FEW MODIFICATIONS new users of **lxde** might enjoy finding in one easy place:

**hotkeys**

[http://wiki.lxde.org/en/LXDE:Questions#Change_hotkeys](http://wiki.lxde.org/en/LXDE:Questions#Change_hotkeys)

** desktop icon size**

pcmanfm->Edit->Preferences->Display->Size of big icons

**Keyboard layout** [Keyboard Languages]

Rightclick on the panel, choose add/remove panel settings. Go to panelapplet, choose "Add" 
Now you have a flag in right corner. Right click on it and choose "Settings for keyboard layout handler" 

**Button Layout**

easy  terminal ```
obconf
```  choose appearance and reorder


or else  in terminal

run   ```
 gedit ~/.config/openbox/lxde-rc.xml
```

ctrl+f   titlelayout

<theme>
  <name>Onyx</name>
  <titleLayout>NLCMI</titleLayout>
  <!--
      available characters are NDSLIMC, each can occur at most once.
      N: window icon
      L: window label (AKA title).
      I: iconify
      M: maximize
      C: close
      S: shade (roll up/down)
      D: omnipresent (on all desktops).

**Mouse Single-click instead of double  **

PCMANFM file manager, and with it open/running go to Edit > Preferences > Behaviour and select "Open Files with single click". 

**Open current file/folder in terminal**   F4  [That easy!]

**Change desktop icon image**

Menu/Pick the Program/Right-click/Properties/Change icon


**File Association**

leafpad  ~/.local/share/applications/mimeapps.list
change say   vlc.desktop   to   totem.desktop

Ctrl+H  then change


**Startup apps  **

go to   ~/.config/autostart

and add a file called nameoftheapp.desktop   and save

looking thus


[Desktop Entry]
Type=Application
Exec=xmms
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_GB]=xmms
Name=xmms
Comment[en_GB]=
Comment=


**Add panel items to top-panel **[for example Browser etc...]

add items to panel


1) Right click on the panel and select "Add/Remove panel items".


2) Select "Application Launch Bar" in "panel applets" sub menu and click "Add".


3) This pops up a window with options to select items from. Again select "Application Launch Bar" from the options and click "Add".


4) This adds a blank "application launch bar" generally at the right end of the panel. Now click on the blank 'application launch bar". This gives you the options to assign the "blank launch bar" to your desired application from the application menu. You can add multiple applications to the same "application launch menu".


**Desktop icon image**      drag into text editor and change path to image




**Cursor theme**    lxappearance








====================

---

### Post by vasa1 on 2013-11-03
@Shantiq, while it's certainly convenient to have several desktop environments available, I feel there could be some disadvantages and I've posted about that here: [http://ubuntuforums.org/showthread.php?t=2183604&p=12828562#post12828562](http://ubuntuforums.org/showthread.php?t=2183604&p=12828562#post12828562).

---

### Post by Frogs Hair on 2013-11-03
***Not  a support request moved to Ubuntu Linux and OS Chat.***

---

### Post by shantiq on 2013-11-03
> **vasa1 said:**
> @Shantiq, while it's certainly convenient to have several desktop environments available, I feel there could be some disadvantages and I've posted about that here: [http://ubuntuforums.org/showthread.php?t=2183604&p=12828562#post12828562](http://ubuntuforums.org/showthread.php?t=2183604&p=12828562#post12828562).


absolutely Vasa;  totally in agreement. I mean one at a time  and not to keep the ones that do not feel good; maybe should have made this clear

---

