---
title: "Ubuntu all Tricked Out"
date: 2008-03-16
forum: The Cafe
---

### Post by rab4567 on 2008-03-16
Hey guys, I'm getting a quite few request on installing ubuntu on computers and I was just wondering is there an easy way to install packages preconfigured and ready to use. You know Compiz Fusion, K3b, Gxine, Streamtuner and so on. This would take less time installing and more time showing people how the programs work.

---

### Post by scragar on 2008-03-16
settings can often just be backed up by copying and pasting several setting files from the ~/ folder:
.purple = pidgin
.kde = all KDE stuff, ./kde/apps for KDE applications
.compiz = compiz settings

you could even make a list of all the programs you normaly install so when you come to set up the computer for someone you can just do a mass install(my freshinstall.sh file looks a little like this:```
sudo apt-get install -y k3b k9copy vlc wine...
```:P

---

### Post by wesley_of_course on 2008-03-16
I keep meaning to try aptoncd but haven't got around to it ,
anybody ? Its in the repo's.

---

### Post by scragar on 2008-03-16
I used it, and it works, provided you don't run apt-clean to clear the cache of installers. Oh, and when it tried it things didn't go well for installing VLC via it.

---

### Post by rab4567 on 2008-03-16
Thanks Dudes.

---

### Post by BobCFC on 2008-03-16
[Creating Custom Ubuntu Live-CD With Remastersys]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html")

or alternatively

[Reconstructor is an Ubuntu GNU/Linux CD Creator]("http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=14&Itemid=37")


not tried either mind you, but they both seem up to date with gutsy.

---

### Post by rab4567 on 2008-03-20
thanks guys

---

### Post by Vadi on 2008-03-20
Here's what I tell every new Ubuntonian to do:

- enable wobbly windows in compiz
- set the number of desktops to 4 instead of the default 2
- enable scale & scale addons, and make the bottom-left Screen Edge to do "Initiate Window Picker for all Windows"
- Enable desktop cube & rotate cube.
- Set the cube transparency while rotating to like 50%, change the default color for the cube (anything but the default... it looks.. ugly)
- enable animations plugin, in there, in the focus animation tab, set it to "dodge" with a 200 delay
- Enable shift switcher, set it to 'cover' switcher mode

That's it for Compiz. Next,
- install flash (*especially* important for 64bit, because on 32 it's easy for the user to do it themself). Test that youtube is working.
- install java
- add medibuntu ([cliick]("http://www.medibuntu.org/")), install the codecs package. Test that mp3 is working.

That's about it. 

Then, teach the user that ctrl+alt+left click, or just a middle-click on the desktop rotate the cube. Tell them that moving the mouse to the bottom-left corner will bring up all windows - in there, right-click on a window to zoom in/out, middle-click to close. windows key + tab does the fancy window switching, win key + scrolling up/down (either on the mouse, or on the right side of the touchpad) will make a window be transparent, while alt+scolling will zoom in/out.

That's about it. If you can get that stuff pre-setup, that would make a great enterance to ubuntu. Well, maybe print the last part with instructions on a paper as a cheatsheet.

---

### Post by macogw on 2008-03-20
man dpkg

look for get-selections and set-selections

---

