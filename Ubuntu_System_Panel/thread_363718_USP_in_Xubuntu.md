---
title: "USP in Xubuntu?"
date: 2007-02-17
forum: Ubuntu System Panel
---

### Post by picpak on 2007-02-17
I've got xfapplet installed, and I'm trying to run USP within Xubuntu 6.10. I try to load it, but all I get this this:

```
'Ubuntu System Panel' could not be loaded.

An internal error occurred and the applet could not be loaded.
```

So then I try to run usp. All I get is:

```
kim@komputer:~$ usp
kim@komputer:~$ 
```

Nothing!!

So, is there anything extra I need to do to get it on Xubuntu? (This is usp 1.91, btw).

---

### Post by Malac on 2007-02-17
> **picpak said:**
> So then I try to run usp. All I get is:```
kim@komputer:~$ usp
kim@komputer:~$ 
```Nothing!!
```
usp run-in-window
``` should show debug messages.

---

### Post by picpak on 2007-02-17
```
kim@komputer:~$ usp run-in-window
kim@komputer:~$
```

It should, shouldn't it.

---

### Post by chanders on 2007-02-17
You should at least see some error...  Try logging out and back in or better yet reboot, and post back...

---

### Post by picpak on 2007-02-17
I reinstalled USP, restarted, and:

```
kim@komputer:~$ usp run-in-window
kim@komputer:~$ 
```

still nothing.

Could it be because I'm using the Xfce 4.4 backports [here](http://ubuntuforums.org/showthread.php?t=350508)?

---

### Post by _linux_ on 2007-02-24
The same thing is happening to me. It's too bad because I really wanted to use USP  in Xubuntu. Oh well.

---

### Post by SubTerRaiN on 2007-04-10
same here... can`t load neither slab, neither usp... :(

---

### Post by Malac on 2007-04-11
I will look into this as I use USP in XFCE/xubuntu too on Edgy.
Though I haven't tried it in Feisty.

---

### Post by Malac on 2007-04-11
Okay I have just logged on to my XFCE Edgy session and all seems to be well.
See Screenie:[ATTACH]29485[/ATTACH]
This is using xfapplet but I started with Ubuntu so I will have dependencies like gconf, gobject and gnome already.
Try installing gnome-panel, gnome-panel-data, gnome-session, gconf2, gconf2-common and gconf-editor see if that helps.

**EDIT:**
Can confirm this works on a Feisty install of Ubuntu then XFCE as well.
I will rig up a test xubuntu install and see if I can sort out what dependencies need resolving.

---

### Post by SubTerRaiN on 2007-04-12
Malac, excellent!

As soon as you get the dependecies for a clean xubuntu install, write`em here, please.

Thanks for ur support.

---

### Post by Malac on 2007-04-12
Okay here goes, this is from a fresh xubuntu install 6.10.
(It shouldn't matter when you do the apt-get install, they could all be on one line, but this is the way I did it.)

**This is the order I did it in:** 
In a terminal: ```
sudo apt-get install subversion xfce4-xfapplet-plugin
cd [COLOR=DimGray]*<to-folder-you-want-the-source>*[/COLOR]
svn checkout http://ubuntu-system-panel.googlecode.com/svn/trunk/ ubuntu-system-panel
cd ubuntu-system-panel
./usp_update install

```Then _before_ you run USP or add it to the panel.
Add the ".usp" folder to your home directory and if you intend to use the "places" plugin create a ".gtk-bookmarks" file in your home directory (although at the moment I can't get this plugin to work properly :( ).
Then :
```

sudo apt-get install python-gnome2 python-gnome2-desktop python-gmenu python-pyinotify gnome-menus
```Then check that no "zombie" instances of USP are running or if you have xfapplet already trying to run a copy of usp remove them.

[COLOR=DimGray]_optional_```
uspconfig
``` to set things like the quit, lock, etc.. commands in system_management and the settings/computer buttons plus other click handling options like thunar instead of nautilus,
e.g.:
"gnome-system-monitor" = "xfce4-taskmanager"
[/COLOR][COLOR=DimGray] "gnome-theme-manager" [/COLOR][COLOR=DimGray] = "xfce-setting-show ui"
[/COLOR][COLOR=DimGray] "gnome-display-properties" = "xfce-setting-show display"
[/COLOR][COLOR=DimGray]"gcontrol" = "xfce-setting-show"

"gnome-screensaver-command --lock" = "xflock4"
"gnome-session-save --kill" = "xfce4-session-logout[/COLOR][COLOR=DimGray]"

[/COLOR] [COLOR=DimGray]These are the ones I know, if you know other replacements pm me with them and I'll update this post.
[/COLOR] 
Add the USP via xfapplet as normal.

I have only tested this on the "standard" plugins uspuser, computer, system_management, applications, recent, places, and shortcuts.
I will get round to checking the "extra/add-on" ones when I have time.
This adds just over 6MB to the xubuntu install with the extra libs the apt-get commands add as dependencies of the packages I've mentioned.

Any probs let me know.
Hope this helps.

---

### Post by SubTerRaiN on 2007-04-13
nice job. lookin` forward for ur updates.

thanks.

---

### Post by picpak on 2007-04-15
I can confirm that this also works in Feisty :) Thanks!

One more thing, after you run the

```
svn checkout http://ubuntu-system-panel.googlecode.com/svn/trunk/ ubuntu-system-panel
```

command, make sure you go to the ubuntu-system-panel/ubuntu-system-panel directory and copy the usr/ folder to the / folder...

---

### Post by Malac on 2007-04-16
> **picpak said:**
> I can confirm that this also works in Feisty :) Thanks!

One more thing, after you run the

```
svn checkout http://ubuntu-system-panel.googlecode.com/svn/trunk/ ubuntu-system-panel
```command, make sure you go to the ubuntu-system-panel/ubuntu-system-panel directory and copy the usr/ folder to the / folder...
thanks picpak, I knew I'd forget something, :) updated guide.

---

### Post by picpak on 2007-04-16
Some more tips for Xubuntu users:

Under "USP Button Icon", put ```
distributor-logo
```
Install catfish, a GTK file searcher. It's in the Feisty universe repo, and you can get a deb for Edgy here: [http://www.getdeb.net/app.php?name=catfish](http://www.getdeb.net/app.php?name=catfish)
Under Applications > Search Command, put ```
catfish SEARCH_STRING
```
Under System Management > Quit, put ```
xfce4-session-logout
``` 
(Xfce 4.4 only.)

The less plugins, the faster the menu. I have my USP down to Applications, User and System Management.

Good luck!

---

