---
title: "My Fluxbox guide"
date: 2007-12-23
forum: Tutorials
---

### Post by -grubby on 2007-12-23
Hello and welcome to my Fluxbox Guide. If you want me to add or edit something just PM me about it and I'll include it with credit to you.

	Here I'll start off with some basic menu editing (See RedSquirrel's awesome guide [here]("http://www.ubuntuforums.org/showthread.php?t=371144")) : 
	BTW, to use your own menu you have to copy /etc/X11/fluxbox/fluxbox-menu to ~/.fluxbox,change your ~/.fluxbox/init file on section "session.menuFile: /etc/X11/fluxbox/menu" to "session.menuFile: ~/.fluxbox/menu" and change ~/.fluxbox/menus section "[include] /etc/X11/fluxbox/fluxbox-menu" to "[include] ~/.fluxbox/menu"

	Now on with **editing your menu**:
>  [exec] 
 basically that's indicating this menu entry will be a program or some other executable-type thing 

after "[exec]" you put :
> (application name) 
this is the application title as will appear in the menu such as "Firefox"

after "(application name)" you put :
> {command-to-run-above-program} 
Here you can specify the command to run the program such as "firefox" or you can sort-of  "link" to an executable (as you could in the terminal) "/usr/bin/firefox" 

after "{command-to-run-program}"  you put :
> </path/to/icon>
This is just the path to the icon that will appear in the menu. It shall be noted that most icons are in /usr/share/pixmaps/. An example of this would be : "</usr/share/pixmaps/firefox/icons/mozicon128.png>"

	So here is the example above (note that the amount of spaces between things like "[exec]" and "(app name)" doesn't matter):
[exec]	    (Firefox)	{firefox)	</usr/share/pixmaps/firefox/icons/mozicon128.png>

	Now here I'll explain **submenus** and how they work:

 	each entry from the paragraph above such as "[exec](Firefox){firefox</usr/share/pixmaps/firefox/icons/mozicon128.png>"  should be put into "submenus" for organization (such as say on GNOME "accessories" or "internet") 

	remember "[exec]" before? well that's basically kind of a "tag" that indicates what the following entries will be. Basically all menu entries with different tags will follow the above format (if not all). 
	so "[submenu]"  creates a submenu without anything else so you have to add them in the following order (as stated above) [submenu] (submenu-name) {} (backgroundjust leave the {command} blank, submenus don't initiate commands) and if you want to use an icon, </path/to/icon>

	After you've added all "[exec]"s into your "[submenu]",you have to make a new line (hit enter) and type "[end]" (which is basically another "tag")
	Also, if you want to make a "[submenu]" within a "[submenu]" you have to add "[end]" to the "[submenu]" within, and another one after the non-within a "[submenu]" "[submenu]"

	So here's an example submenu with execs in it:
```
 
[submenu] (Internet) {}  </usr/share/pixmaps/ubuntu.xpm>
[exec]        (Firefox)        {firefox}  </usr/share/pixmaps/firefox.png>
[exec]        (Konqueror)   {konqueror} </usr/share/pixmaps/konqeror.xpm>
    [submenu]  (Instant-Messengers) {} </usr/share/pixmaps/gajim.png>
    [exec]         (Gajim)  {gajim} </usr/share/pixmaps/gajim.png>
    [exec]         (Gossip) {gossip} </usr/share/pixmaps/gossip/icons/gossip.xpm>
    [exec]         (Pidgin)  {pidgin}   </usr/share/pixmaps/pidgin.xpm>
[end]
[exec]        (Skype)      {skype}     </usr/share/pixmaps/skype.xpm>
[exec]        (Thunderbird) {thunderbird} </usr/share/thunderbird/thunderbird.png>
[end]

```

UPDATE: you can also add separators between menu entries add the "tag" [separator] between menu entries
UPDATE: you can also add spaces between menu entries add the "tag" [nop] SOURCE: teaswigger
SOURCE: the source person wished to receive no credit 
Note: I would like some further help with menus and different "tags" (such as "[restart]")

	**The Startup file**. You can locate this in ~/.fluxbox/startup:

	basically all this is is pretty much running programs or executable thingies (like commands) on startup. So here yah go:

	To keep a command running (example: running "sudo /etc/init.d/alsa-utils restart" is not a command that keeps running) add an and (&) sign after the entry. Example:
firefox &
Easy as pie.
	Moving on: here's the command to set a wallpaper to use on startup:

fbsetbg -f /path/to/wallpaper/
	Sometimes you can have lots and lots of directories to plough through (like me, I organize too much) and it can be painful. In this case I would recommend setting links to the wallpaper, but if for some reason not, it's not too painful  to manually *sigh* set the path to the wallpaper.

Note: you can read all of what I said in this startup section in the ~./fluxbox/startup file's comments (lines that start with a pound sign '#')

End of the "startup file section"

	**Icons**: You may have seen  icons on fluxbox desktops and are wondering how to get them, I will explain in the section ahead
	When I first wanted icons, I used the program "fbdesk", but I, for some reason, could not find where to edit the config files for it. Because of the aforementioned reasons, I recommend "idesk" 
	After you've installed idesk, you probably will want to add it to your startup file (above) so you can have icons each boot without having to run it from a terminal, but, before idesk will run, you have to make a .idesktop folder in your home directory. 
	Now that (I assume) you've done that,  you will want to add icons, I'll explain:

	this is what an idesk icon file looks like:
```

table Icon
  Caption: Home
  Command: thunar /home/nathan
  Icon: /usr/share/idesk/folder_home.xpm
  Width: 48
  Height: 48
  X: 33
  Y: 27
end

```
	First of all, to add an icon, you have to create a file for it called  "insert-your-file-name-here.lnk" and follow the idesk icon file above (the config is pretty straightforward, the only thing that may confuse you is "table Icon" basically you just add that to the top of each icon file you create (make sure the "I" on "Icon" is capitalized, and that the "t" in "table", is not)
 
end of "icon section"

	Styles: To change the style is pretty easy, just create a "styles" directory under ~/.fluxbox
and find styles you want (some can be found on [http://www.box-look.org](http://www.box-look.org)) and extract the archive. then move the extracted folder to ~/.fluxbox/styles and it should show up under the submenu (depending on how your fluxbox menu is configured) "styles"

end of "style section"

	**Changing your QT or GTK theme** under fluxbox:

You can change your GTK and/or QT4/QT3 theme under fluxbox, just install the following:
gtk-chtheme (for GTK)
qt4-qtconfig (for  QT4) (for some reason, the command to run this is "qt-qt4config"
qt3-qtconfig  (for QT3)  (as above, the command to run this is "qt-qt3config"

end of "GTK/QT theme section"

	**File Managers**: 

File managers are pretty straightforward in fluxbox, just use your favorite one (I recommend thunar) but it's important to mention here that to run nautilus you have to run "nautilus --no-desktop" or else your current fluxbox section will be all screwed up

end of  "file manager section"

         **Extras**
UPDATE: I also just remembered to add this: you can tab whole windows (gedit,thunar,firefox,etc) by middle clicking (holding down the left and right buttons if you don't have a middle button) and dragging it onto the window you want it to tab to

BTW, This is my first tutorial, what do you think?

My menu file (for reference) attached

---

### Post by dnns123 on 2007-12-23
This should be in tutorial section :)

---

### Post by -grubby on 2007-12-23
oh well I must've missed it. Could a mod could move it please?
EDIT: They moved it. Thanks guys!

---

### Post by -grubby on 2007-12-25
bump

---

### Post by Drone4four on 2007-12-26
In Gnome, Alt + F3 is the run command.  Similarly, in e17, the run command is Ctrl + Esc.  What is the run command in Fluxbox?

---

### Post by BLTicklemonster on 2007-12-26
install and set up xkeybinds to run it any way you want.

Great, helpful and useful thread. Thanks!

---

### Post by -grubby on 2007-12-27
> **Drone4four said:**
> In Gnome, Alt + F3 is the run command.  Similarly, in e17, the run command is Ctrl + Esc.  What is the run command in Fluxbox?

fluxbox doesn't have a run dialog. You can install (oh man I don't remember right now, I used to run one) I guess I'll get back later with the name
EDIT: now I remember: bbrun

---

### Post by TeaSwigger on 2007-12-28
> **Drone4four said:**
> In Gnome, Alt + F3 is the run command.  Similarly, in e17, the run command is Ctrl + Esc.  What is the run command in Fluxbox?

Fluxbox has a very fast & simple run box called fbrun. It should be installed by default already if you're using the version in the ubuntu repositories. To use it from the keyboard, set any keybinding you want and put it in ~/.fluxbox/keys. Create this file if it's not there. As an example here is what I have.

```
Mod4 r :Exec /usr/bin/fbrun
```

This means: Mod4 is the "windows" key. "r" simply is the r key. :Exec is where you put what you want to run from those keys, in this case I put the path to fbrun. So I press "windows key+r" and it pops up.

You could also add it to your fluxbox menu. Here is how I have it:

```
[exec] (Run Program (fbrun\)) {/usr/bin/fbrun}
```

fbrun remembers your previous entries. Just use the arrow keys to scroll. They're stored in a text file at ~/.fluxbox/fbrun_history.

---

### Post by TeaSwigger on 2007-12-28
nathangrubb, if I may, you could add another bit to the menu guide. There's [nop] which will put in a non-active line of text in the menu for a separator. Like this, from the Development section of my "hand-rolled" menu at the moment::

```
[submenu] (Development)
	[exec] (XAMPP Control Panel) {kdesu "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"}
	[nop] (WebDev Environments)
	[exec] (Quanta Plus) {/usr/bin/quanta}
	[exec] (KompoZer) {/usr/bin/kompozer}
	[nop] (Utilities)
	[exec] (Cervisia - CVS) {cervisia}
	[exec] (EmbedJS) {/usr/bin/embedjs}
	[exec] (Kdiff3) {/usr/bin/kdiff3}
	[exec] (KHexEdit) {/usr/bin/khexedit}
	[exec] (KFileReplace) {/usr/bin/kfilereplace}
	[exec] (KImageMapEditor) {/usr/bin/kimagemapeditor}
	[exec] (KLinkStatus) {/usr/bin/klinkstatus}
	[exec] (Kommander Editor) {/usr/bin/kmdr-editor}
	[exec] (Komparator) {/usr/bin/komparator}
	[exec] (Kompare) {/usr/bin/kompare}
	[exec] (KRename) {/usr/bin/krename}
	[exec] (KXML Editor) {/usr/bin/kxmleditor}
	[exec] (KXSLDbg - XSLD Debugger) {/usr/bin/kxsldbg}
[end]
```

---

### Post by -grubby on 2007-12-30
> **TeaSwigger said:**
> nathangrubb, if I may, you could add another bit to the menu guide. There's [nop] which will put in a non-active line of text in the menu for a separator. Like this, from the Development section of my "hand-rolled" menu at the moment::

```
[submenu] (Development)
	[exec] (XAMPP Control Panel) {kdesu "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"}
	[nop] (WebDev Environments)
	[exec] (Quanta Plus) {/usr/bin/quanta}
	[exec] (KompoZer) {/usr/bin/kompozer}
	[nop] (Utilities)
	[exec] (Cervisia - CVS) {cervisia}
	[exec] (EmbedJS) {/usr/bin/embedjs}
	[exec] (Kdiff3) {/usr/bin/kdiff3}
	[exec] (KHexEdit) {/usr/bin/khexedit}
	[exec] (KFileReplace) {/usr/bin/kfilereplace}
	[exec] (KImageMapEditor) {/usr/bin/kimagemapeditor}
	[exec] (KLinkStatus) {/usr/bin/klinkstatus}
	[exec] (Kommander Editor) {/usr/bin/kmdr-editor}
	[exec] (Komparator) {/usr/bin/komparator}
	[exec] (Kompare) {/usr/bin/kompare}
	[exec] (KRename) {/usr/bin/krename}
	[exec] (KXML Editor) {/usr/bin/kxmleditor}
	[exec] (KXSLDbg - XSLD Debugger) {/usr/bin/kxsldbg}
[end]
```

I was planning to include that but  I couldn't remember if it was called  [nap] or [nop] so I'll include it now

---

### Post by Drone4four on 2008-01-16
> **TeaSwigger said:**
> Fluxbox has a very fast & simple run box called fbrun. It should be installed by default already if you're using the version in the ubuntu repositories. To use it from the keyboard, set any keybinding you want and put it in ~/.fluxbox/keys. Create this file if it's not there. As an example here is what I have.

```
Mod4 r :Exec /usr/bin/fbrun
```

This means: Mod4 is the "windows" key. "r" simply is the r key. :Exec is where you put what you want to run from those keys, in this case I put the path to fbrun. So I press "windows key+r" and it pops up.

You could also add it to your fluxbox menu. Here is how I have it:

```
[exec] (Run Program (fbrun\)) {/usr/bin/fbrun}
```

fbrun remembers your previous entries. Just use the arrow keys to scroll. They're stored in a text file at ~/.fluxbox/fbrun_history.

fbrun isntalled just fine on my ubuntu box in Toronto...but in Peterborough, fbrun isn't in the ubuntu repos:```
drone4four@ubuntu:~$ sudo apt-get install fbrun
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package fbrun
drone4four@ubuntu:~$ sudo apt-get install fb
fbb            fbgrab         fblogo         fbpager        fbtv
fbbdoc         fbi            fb-music-high  fbpanel        fbxkb
fbdesk         fbiterm        fb-music-low   fbset  
```

---

### Post by Belak on 2008-03-19
@Drone4four:
fbrun should be installed by default with fluxbox... especially with the one in the repos.

@The topic starter (sorry... too lazy to look back)
Anyway, in your menu file, shouldn't the ```
[exec]    (-------------)          {}
```
be
```
[nop] (-------------) <>
```

---

### Post by -grubby on 2008-05-01
> **Belak said:**
> 
@The topic starter (sorry... too lazy to look back)
Anyway, in your menu file, shouldn't the ```
[exec]    (-------------)          {}
```
be
```
[nop] (-------------) <>
```

Sorry for taking so long to respond. 
Yes it should, I won't bother to fix it, though. Though I don't believe the "<>" is needed, as it's set to nothing by default

---

### Post by tyrant92 on 2012-04-18
> **-grubby said:**
> Hello and welcome to my Fluxbox Guide. If you want me to add or edit something just PM me about it and I'll include it with credit to you.

	Here I'll start off with some basic menu editing (See RedSquirrel's awesome guide [here]("http://www.ubuntuforums.org/showthread.php?t=371144")) : 
	BTW, to use your own menu you have to copy /etc/X11/fluxbox/fluxbox-menu to ~/.fluxbox,change your ~/.fluxbox/init file on section "session.menuFile: /etc/X11/fluxbox/menu" to "session.menuFile: ~/.fluxbox/menu" and change ~/.fluxbox/menus section "[include] /etc/X11/fluxbox/fluxbox-menu" to "[include] ~/.fluxbox/menu"



I think there is a mistake in the instruction in ~/.fluxbox/menu section. I think the [include] part should be changed to ~/.fluxbox/fluxbox-menu, not ~/.fluxbox/menu. Right?

---

