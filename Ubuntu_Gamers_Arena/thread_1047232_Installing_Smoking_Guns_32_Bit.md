---
title: "Installing Smoking Guns 32 Bit"
date: 2009-01-22
forum: Ubuntu Gamers Arena
---

### Post by michaelrg1231 on 2009-01-22
Download the game: [http://www.smokin-guns.net/template.php?page=11&sid=cb28b5bbf75707a47ff5a1885a678665](http://www.smokin-guns.net/template.php?page=11&sid=cb28b5bbf75707a47ff5a1885a678665)

To install the game:

      * Get the ZIP package
      * Unzip it in your home folder
      * Rename the base folder from "Smokin' Guns" to "SmokinGuns" as the engine will always look for that folder as installed game path.
      * in the folder make sure "smokinguns.x86" has the execution right ("chmod +x smokinguns.x86" from a console will fix that)


Then you can run "smokinguns.x86" from anywhere.
For example, you can create a link on your desktop pointing to "~/SmokinGuns/smokinguns.x86" and just have to click on it to start the game.

Also make sure you have opengl and openal drivers installed in their 32bits version. 

Creating a start menu item

Right Click menu bar, Edit menus
Under Games Add new Item

Under Type: Application
Under Name: Smokin' Guns
Under Command: /home/"your user name"/SmokinGuns/smokinguns.x8

Comment if deemed necessary 

Icon:/home/"your user name"/SmokinGuns/sg_48.png

To play Applications-Games-SmokingGuns

---

### Post by Alexcostaricha on 2009-03-03
I did so but it doesn't work. Can you help me please ?
Must I have Quake III for beginning?
I downloaded OpenArena to make sure...

---

### Post by JohnCaper on 2009-03-06
I can get it to start but then the graphics go nuts, I loose letters & numbers, things are fuzzy etc. Any suggestions?

---

### Post by Yeti can't ski on 2009-03-21
Hey Guys, 

I was also stuck with the install, but then I found the following instructions/commands in a separate forum:

sudo apt-get install libopenal1
sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so
sudo ln -s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0

After that the game worked just like magic. 

Here is where I found it: [http://nousessence.com/node/1257](http://nousessence.com/node/1257)

Good luck!

Yeti

---

