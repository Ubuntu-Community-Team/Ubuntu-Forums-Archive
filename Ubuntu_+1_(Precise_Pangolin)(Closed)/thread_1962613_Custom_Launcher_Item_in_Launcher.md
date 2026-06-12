---
title: "Custom Launcher Item in Launcher"
date: 2012-04-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ewangr on 2012-04-21
OK, I have a development tool for a game I'm working on called "Ren'Py" that is invoked by running a script "renpy.sh". I can execute the script from my home folder and the tool starts up fine. I see the icon over in my launcher on the left, and my environment is opened so I can begin editing.

I have used the Lock to Launcher option to add it to the left side launchbar. But if I try to start it the icon "blinks" as an icon does when it starts, but then it keeps blinking for a moment, and then nothing happens.

My presumption is that when starting from the launcher it is using the wrong directory or some other environmental variable is getting munged. Rather than edit the .sh file (since I'd like to avoid having to do this for every release of the tool), is there some way to edit the Launcher item to specify how it is called? It certainly seems like that SHOULD be an option, but danged if I can find it.

---

### Post by hakermania on 2012-04-21
Hello!
Open a terminal (Ctrl+Alt+T) and give:
```

gsettings get com.canonical.Unity.Launcher favorites

```This will show all your launchers that you have attached to the unity bar on the left in a row (placed from top to bottom).

Check the name of the launcher used to launch your application, and copy it to your clipboard for later use.

Now, through the terminal again navigate to /usr/share/applications:
```

cd /usr/share/applications

```and then
```

gksudo gedit [paste here what you have in your clipboard]

```in order to open the file with root access and edit it.

You will probably see something like this:
```

[Desktop Entry]
Version=2.1
Name=Wallch
Comment=Change desktop wallpapers automatically
Exec=/usr/bin/wallch
Icon=wallch
Terminal=false
Type=Application
Categories=Utility;Application;
MimeType=application/x-wallch-project

```and as I understood from your post, the "Exec=" field is wrong! So, change this field and set it to the right path pointing to the script! Save the file, and you should be ready!

Hope I helped!

---

### Post by ewangr on 2012-04-21
Following your first command I get the following:

```

gsettings get com.canonical.Unity.Launcher favorites
['nautilus-home.desktop', 'libreoffice-writer.desktop', 'ubuntu-software-center.desktop', 'gnome-terminal.desktop', 'xscreensaver-properties.desktop', 'gnome-control-center.desktop', 'gnome-system-monitor.desktop', 'google-chrome.desktop']

```
The Renpy item shows up after the Chrome icon which is the last one on the list above.

Going to /usr/share/applications anyway, I do not see anything that is intuitively obvious that might represent the item.

Other ideas?

---

### Post by mc4man on 2012-04-21
Your app doesn't appear to provide a .desktop file so you'd need to create one
You could either then add it to the launcher Or make the .desktop executable & just use it to launch your app by d. clicking on

The issue(s) you'll see if you add it to the launcher are 2

While it will launch the app it won't control it, a 2nd icon will appear, the same one you see now when running renpy.sh
This is basically because it's using a script to run another script

2nd -  the available icons don't seem to scale well to the launcher while when renpy runs it does (unless I'm missing one

So the best solution may be to open renpy from a quicklist added to an existing .desktop you have on the launcher. It could be added to any one or if desired you could create a 'categorized' launcher where the quicklists open apps of a like type

So - an Ex. of a standalone .desktop (launcher) could be as simple as this, the red need to reflect actual paths you have, blue can be anything you wish
```
gedit ~/Desktop/renpy.desktop
```

```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=[COLOR="Red"]/home/doug/Desktop[/COLOR]/renpy/renpy.sh
Name=[COLOR="Blue"]Renpy[/COLOR]
Icon=[COLOR="Red"]/home/doug/Desktop/[/COLOR]renpy/launcher/[COLOR="Blue"]logo.png[/COLOR]
```

If used as a launcher not in the unity launcher just r. click on > properties >permissions > allow exec...

if your intention was to use it in the unity launcher even with the 2 issues then instead of creating on your Desktop create it here, then DnD onto the launcher, no need to make executable, assumes that dir. exists. if not then create
```
gedit ~/.local/share/applications/renpy.desktop
```

I think that unless you can resolve the 2 icon deal that opening from a quiclist is best way.
There is a script here that will assist you though it's limited to quicklist editing on certain .desktops
[http://ubuntuforums.org/showthread.php?t=1961642](http://ubuntuforums.org/showthread.php?t=1961642)

If you had an existing one in mind that's not on that list just post or if standard post it's name - will edit for you, once you see it's a piece of cake (if so post path to renpy.sh

Or you can create a new category based icon - easy to once you get the idea - I'll post an example of that where I added renpy even though may not fit the category,  if I had more of similar types I'd  probably would make a new one.

---

### Post by mc4man on 2012-04-21
Example of a Category based unity launcher - 
In this case it's named Utilities
The left click on the icon will run synaptic, used that because it's the most often used one.
The quicllists just are other apps & a couple of scripts in ~/bin (htop1 & update1)  & 1 command, xkill

So added renpy - The location of the [Desktop Action Whatever ] section  is irrelevant, position in launcher is determined by position on the Action= line
(as is the appearance of  - if I wanted to remove a quicklist for the moment I'd just remove it from the Action= line & leave the section

```
[Desktop Entry]
Version=1.0 
Type=Application
Terminal=false
Exec=synaptic-pkexec
Name=Utilities
Icon=/usr/share/icons/Humanity/categories/48/applications-other.svg
Actions=CCSM;Htop;GetUp;NaTool;Dconf;Gconf;UM;FQuit;SS;Seach;Renpy;

[Desktop Action Renpy]
Name=Renpy Launcher
Exec=[COLOR="Red"]/home/doug/Desktop[/COLOR]/renpy/renpy.sh
TargetEnvironment=Unity

[Desktop Action Htop]
Name=Htop
Exec=htop1
TargetEnvironment=Unity

[Desktop Action GetUp]
Name=Update Sources
Exec=update1
TargetEnvironment=Unity

[Desktop Action NaTool]
Name=Nautilus Actions
Exec=nautilus-actions-config-tool
TargetEnvironment=Unity

[Desktop Action CCSM]
Name=Compiz Settings
Exec=ccsm
TargetEnvironment=Unity

[Desktop Action Gconf]
Name=Gconf Editor
Exec=gconf-editor
TargetEnvironment=Unity

[Desktop Action FQuit]
Name=Force Quit
Exec=xkill
TargetEnvironment=Unity

[Desktop Action SS]
Name=Screen Shots
Exec=gnome-screenshot --interactive
TargetEnvironment=Unity

[Desktop Action Seach]
Name=Search For Files
Exec=gnome-search-tool
TargetEnvironment=Unity

[Desktop Action Dconf]
Name=Dconf Editor
Exec=dconf-editor
TargetEnvironment=Unity

[Desktop Action UM]
Name=Update Manager
Exec=/usr/bin/update-manager
TargetEnvironment=Unity
```

---

