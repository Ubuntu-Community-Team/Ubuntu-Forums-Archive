---
title: "Conkyrc changer for Obmenu"
date: 2008-08-14
forum: The Cafe
---

### Post by elbeem on 2008-08-14
Hi! This is my first post at Ubuntuforums. I didn't know where to post, so I posted it here. Earlier this evening I was looking for a conkyrc changer for the Openbox menu. Since I didn't find anything, I decided to make one for myself. Here is the result:

[SIZE="5"]conkyrc changer for Obmenu[/SIZE]

Use this scipt if you use a lot of conkyrc-files. I change wallpapers quite often, and by having the same conkyrc-file in different colors my Conky will allways be visible.

[SIZE="3"]Usage[/SIZE]

1. Make a folder ~/.config/conkyrc
2. Place all your conkyrc files in this folder. The filenames doesn't matter. The file ~/.conkyrc will be replaced, so just move it to this folder.
3. Move the conkyrc.py-file that is included in this post to a place where you have all your Obmenu script files. (e.g. ~/.config/openbox/bin/)
4. Make this entry in ~/.config/openbox/menu.xml:

<menu execute="python ~/.config/openbox/bin/conkyrc.py" id="conkyrc" label="conkyrc"/>

Change the script path if necessary. You can also change label="conkyrc" to something you prefer.

5. Restart Openbox and enjoy! :) This menu can also be used as a Conky launcher.

[SIZE="3"]How it works[/SIZE]

When you select an entry in the menu, the script copies the conkyrc file to your home directory and renames the file to ".conkyrc", replacing any existing file. This way, the conky theme will not change back upon rebooting. When the file has been copied, the command "conky -c ~/.config/conkyrc/SELECTED_FILE" will run.

Thanks for any feedback!

---

### Post by picpak on 2008-08-14
Sounds good. :)

I wish I knew Python. Now all we need is a GUI for keybindings and autostart.sh and Openbox would be perfect :)

---

